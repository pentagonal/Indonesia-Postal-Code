# Indonesia Postal & Province Code

## Contains:

```
34      - Provinces
81.248  - Areas (Postal Codes)
```
## DATA TYPE

`MySQL Database Syntax` ( see at ) [https://www.mysql.com/](https://www.mysql.com/)

## MySQL Database To Import
```
postal_province_table.sql
```

## Import With CLI

```bash
mysql -u [userName] -p [databaseName] < postal_province_table.sql
```

Note :

```txt
`[userName]`      : MySQL User That Granted Access For Database
`[databaseName]`  : Database Name target to import.
```
Or just doing import process with `phpMyAdmin`


## REFERENCES
The SQL Dump contains drop tables

```sql
DROP TABLE IF EXISTS `db_province_data`;
DROP TABLE IF EXISTS `db_postal_code_data`;
```

Please make sure delete the lines (on `postal_province_table.sql` ) or backup database before doing import process.


## PROVINCES REFERENCES
```json
{
    "11" : "ACEH",
    "12" : "SUMATERA UTARA",
    "13" : "SUMATERA BARAT",
    "14" : "RIAU",
    "15" : "JAMBI",
    "16" : "SUMATERA SELATAN",
    "17" : "BENGKULU",
    "18" : "LAMPUNG",
    "19" : "KEPULAUAN BANGKA BELITUNG",
    "21" : "KEPULAUAN RIAU",
    "31" : "DAERAH KHUSUS IBUKOTA JAKARTA",
    "32" : "JAWA BARAT",
    "33" : "JAWA TENGAH",
    "34" : "DAERAH ISTIMEWA YOGYAKARTA",
    "35" : "JAWA TIMUR",
    "36" : "BANTEN",
    "51" : "BALI",
    "52" : "NUSA TENGGARA BARAT",
    "53" : "NUSA TENGGARA TIMUR",
    "61" : "KALIMANTAN BARAT",
    "62" : "KALIMANTAN TENGAH",
    "63" : "KALIMANTAN SELATAN",
    "64" : "KALIMANTAN TIMUR",
    "65" : "KALIMANTAN UTARA",
    "71" : "SULAWESI UTARA",
    "72" : "SULAWESI TENGAH",
    "73" : "SULAWESI SELATAN",
    "74" : "SULAWESI TENGGARA",
    "75" : "GORONTALO",
    "76" : "SULAWESI BARAT",
    "81" : "MALUKU",
    "82" : "MALUKU UTARA",
    "91" : "PAPUA",
    "92" : "PAPUA BARAT",
}
```

## EXAMPLE MYSQL CODE TO USE BOTH TABLE

```sql
SELECT
  `db_postal_code_data`.*,
  `db_province_data`.`name` AS `province_name`
FROM
  `db_postal_code_data`
INNER JOIN
  `db_province_data` ON `db_province_data`.`code` = `db_postal_code_data`.`province_code`
WHERE
  `db_province_data`.`code` = 11
ORDER BY
  `db_postal_code_data`.`id` DESC
LIMIT 10 OFFSET 0
```

EXAMPLE OUTPUT

```txt
+------+--------------+----------------------+--------------+---------------+-------------+---------------+
| id   | urban        | sub_district         | city         | province_code | postal_code | province_name |
+------+--------------+----------------------+--------------+---------------+-------------+---------------+
| 6464 | YUB MEE      | INDRAJAYA            | PIDIE        |            11 | 24171       | ACEH          |
| 6463 | WUE LHOK     | MANTASIEK (MONTASIK) | ACEH BESAR   |            11 | 23362       | ACEH          |
| 6462 | WONOSOBO     | WIH PESAM            | BENER MERIAH |            11 | 24581       | ACEH          |
| 6461 | WONOSARI     | BANDAR               | BENER MERIAH |            11 | 24582       | ACEH          |
| 6460 | WONO SARI    | TAMIANG HULU         | ACEH TAMIANG |            11 | 24478       | ACEH          |
| 6459 | WIHNI DURIN  | SYIAH UTAMA          | BENER MERIAH |            11 | 24582       | ACEH          |
| 6458 | WIHNI DURIN  | SILIH NARA           | ACEH TENGAH  |            11 | 24562       | ACEH          |
| 6457 | WIHNI BAKONG | SILIH NARA           | ACEH TENGAH  |            11 | 24562       | ACEH          |
| 6456 | WIHLAH SETIE | BINTANG              | ACEH TENGAH  |            11 | 24571       | ACEH          |
| 6455 | WIH TERJUN   | PEGASING             | ACEH TENGAH  |            11 | 24561       | ACEH          |
+------+--------------+----------------------+--------------+---------------+-------------+---------------+
```

## NOTE (Indonesia)

- urban : kelurahan
- sub_district : kecamatan
- city: kota
- province_code : Kode Provinsi ( Standar)
- id : increment number / kode urut otomatis susunan SQL

## LINK
- [https://github.com/edwin/database-kodepos-seluruh-indonesia/](https://github.com/edwin/database-kodepos-seluruh-indonesia/)
- [http://kodepos.posindonesia.co.id/](http://kodepos.posindonesia.co.id/)

## LICENSE
MIT @see [LICENSE](LICENSE)

