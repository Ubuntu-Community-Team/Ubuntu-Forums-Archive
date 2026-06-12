---
title: "upgrade PHP-mysql"
date: 2006-07-30
forum: General Help
---

### Post by LordMerlin on 2006-07-30
Hey all

How do I upgrade the PHP-mysql client?

This is from phpinfo()

```

**mysql**

  MySQL Supportenabled Active Persistent Links 0  Active Links 0  Client API version 4.0.24  MYSQL_MODULE_TYPE external  MYSQL_SOCKET /var/run/mysqld/mysqld.sock  MYSQL_INCLUDE -I/usr/include/mysql  MYSQL_LIBS -L/usr/lib -lmysqlclient
```

Yet, running  aptitude install mysql-client-4.1 mysql-common-4.1 doesn't upgrade it:

root@Gimbli:~# mysql -V
mysql  Ver 14.7 Distrib 4.1.12, for pc-linux-gnu (i486) using readline 4.3

---

