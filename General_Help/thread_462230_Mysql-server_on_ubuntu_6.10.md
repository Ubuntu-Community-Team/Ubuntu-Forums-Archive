---
title: "Mysql-server on ubuntu 6.10"
date: 2007-06-02
forum: General Help
---

### Post by illuz1on on 2007-06-02
hey,

having the following trouble after installing mysql-server via apt-get.. please anyone gimme a hand! :) thanks

chris@chris-laptop:/var/run/mysqld$ mysqld
070602 19:57:13 [Warning] One can only use the --user switch if running as root

070602 19:57:13  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
chris@chris-laptop:/var/run/mysqld$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
chris@chris-laptop:/var/run/mysqld$ mysqld_safe --user=mysql &
[1] 7811
chris@chris-laptop:/var/run/mysqld$ Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[7872]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[7881]: ended

[1]+  Done                    mysqld_safe --user=mysql
chris@chris-laptop:/var/run/mysqld$

---

### Post by eggdeng on 2007-06-02
Should be able to log on with ```
mysql -u root mysql
```
```
mysqld
``` 
gives me exactly the same output on my working installation.

---

### Post by eggdeng on 2007-06-02
sorry, dupe

---

