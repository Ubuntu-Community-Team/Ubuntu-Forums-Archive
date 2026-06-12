---
title: "pure-ftpd-mysql uses wrong username to mysql"
date: 2007-09-17
forum: General Help
---

### Post by cbox on 2007-09-17
I have configured pure-ftpd-mysql to conect to my MySQL database with the username ftp.

Although this is configured and i can see it uses the MySQL file, it tries to connect to the database with username root.

Startup command:
/usr/sbin/pure-ftpd-mysql -l mysql:/etc/pure-ftpd/db/mysql.conf -u 1000 -E -j -d -O w3c:/var/log/pureftpd.log -B

Log from MySQL:
479 Connect     Access denied for user 'root'@'localhost' (using password: YES)

Config:
MYSQLSocket     /var/run/mysqld/mysqld.sock
MYSQLUser      ftp

What could be the reason for this?

---

