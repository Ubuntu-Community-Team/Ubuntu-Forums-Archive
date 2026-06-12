---
title: "Mysqldump cannot connect “permission denied”"
date: 2020-07-27
forum: General Help
---

### Post by baz42 on 2020-07-27
Ubuntu 18.04
10.1.44-MariaDB-0ubuntu0.18.04.1

I’m trying to backup one of DBs:
```
mysqldump --single-transaction -h localhost -u root -p DBname > ./nxc-lv_20200727.bak
Enter password:
mysqldump: Got error: 2002: "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13 "Permission denied")" when trying to connect
```
dmesg:
```
[66791.515094] audit: type=1400 audit(1595830991.140:283): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/etc/mysql/mariadb.cnf" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[66791.515121] audit: type=1400 audit(1595830991.140:284): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/etc/mysql/conf.d/" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[66791.515228] audit: type=1400 audit(1595830991.140:285): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/etc/mysql/conf.d/mysql.cnf" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[66791.515273] audit: type=1400 audit(1595830991.144:286): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/etc/mysql/conf.d/mysqldump.cnf" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[66791.515315] audit: type=1400 audit(1595830991.144:287): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/etc/mysql/mariadb.conf.d/" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[66791.515375] audit: type=1400 audit(1595830991.144:288): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/etc/mysql/mariadb.conf.d/50-client.cnf" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[66791.515423] audit: type=1400 audit(1595830991.144:289): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/etc/mysql/mariadb.conf.d/50-mysql-clients.cnf" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[66791.515461] audit: type=1400 audit(1595830991.144:290): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/etc/mysql/mariadb.conf.d/50-mysqld_safe.cnf" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[66791.515498] audit: type=1400 audit(1595830991.144:291): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/etc/mysql/mariadb.conf.d/50-server.cnf" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[66791.516170] audit: type=1400 audit(1595830991.144:292): apparmor="ALLOWED" operation="open" profile="/usr/bin/mysqldump" name="/usr/share/mysql/charsets/Index.xml" pid=11886 comm="mysqldump" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```
ls -l /var/run/mysqld/:
```
total 4
-rw-rw---- 1 mysql mysql 6 &#1080;&#1102;&#1083; 27 09:23 mysqld.pid
srwxrwxrwx 1 mysql mysql 0 &#1080;&#1102;&#1083; 27 09:23 mysqld.sock
```

DB is work well. I can login with ‘mysql -u root -p’ and via phpmyadmin. But it doesn’t work with mysqldump.
Please help.

---

### Post by baz42 on 2020-07-27
Figured out.
"sudo -u mysql mariabackup" has made DB backup.
"sudo -u mysql mysqdump" doesn't work.

---

