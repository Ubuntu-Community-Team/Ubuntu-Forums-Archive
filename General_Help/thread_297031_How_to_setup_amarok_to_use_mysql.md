---
title: "How to setup amarok to use mysql?"
date: 2006-11-10
forum: General Help
---

### Post by mmcmonster on 2006-11-10
Hi.
  I was wondering how to setup amarok to use mysql.
  I've installed amarok and mysql, but don't know how to setup mysql properly.  I've been using Ubuntu for about a year, but I'm a database newbie, so simple instructions would be nice.


If it makes a difference, I'm running Dapper.

---

### Post by msak007 on 2006-11-11
[This]("http://amarok.kde.org/wiki/MySQL_HowTo#MySQL_Setup") is the guide from Amarok's web site that I used when I set up Amarok / MySQL several months ago. Hope it helps.

---

### Post by mmcmonster on 2006-11-11
> **msak007 said:**
> [This]("http://amarok.kde.org/wiki/MySQL_HowTo#MySQL_Setup") is the guide from Amarok's web site that I used when I set up Amarok / MySQL several months ago. Hope it helps.

Thanks a lot.  I've got it working now.

One question: How can I tell if the mysql server is going to startup next time I reboot the computer?

---

### Post by msak007 on 2006-11-11
No problem, glad you got it working. AFAIK, MySQL automatically runs as a service at startup in Dapper, or when needed in Edgy (new event-driven init system).

---

### Post by dorcssa on 2007-01-04
```
mysql> \set password for root@localhost = password('xxxxx')
--------------
mysql  Ver 14.12 Distrib 5.0.22, for pc-linux-gnu (i486) using readline 5.1

Connection id:          5
Current database:
Current user:           root@localhost
SSL:                    Not in use
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.0.22-Debian_0ubuntu6.06.2-log
Protocol version:       10
Connection:             Localhost via UNIX socket
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    latin1
Conn.  characterset:    latin1
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 20 min 36 sec

Threads: 1  Questions: 22  Slow queries: 0  Opens: 0  Flush tables: 1  Open tables: 6  Queries per second avg: 0.018
--------------

    -> flush privileges
    -> \flush privileges
ERROR:
Unknown command '\f'.

```

I no nothing about mysql, and tried to configure it via that amarok howto page. Can somebody help me to solve my problem? I heard that mysql db is better than the built in one.

I'm getting really confused...

```
doribaba@zsoltibaba:~$ mysqladmin -u root password your-new-password
doribaba@zsoltibaba:~$ mysqladmin -u root password xxxx
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
doribaba@zsoltibaba:~$ sudo mysqladmin -u root xxxxx xxxxx
Password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
doribaba@zsoltibaba:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
doribaba@zsoltibaba:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
doribaba@zsoltibaba:~$ mysql -u root xxxxx
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
doribaba@zsoltibaba:~$ mysqladmin -u root password xxxxx
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
doribaba@zsoltibaba:~$ sudo mysqladmin -u root password xxxxx
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
doribaba@zsoltibaba:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
doribaba@zsoltibaba:~$
``` I tried to use the ubuntuguide.org version of pass-setup, but I think I don't know what I'm doing. :(

---

### Post by VanHammersly on 2007-02-09
Maybe you'll find this link helpful in setting up amarok to use mysql.

[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

Good Luck.

---

### Post by ifross on 2007-02-09
in the mysql prompt, you need to end each line with a ";"

---

### Post by nichpakaich on 2008-03-23
my problem is, everytime I set the MySQL database (in Amarok) along with the user and password. It keep accessing the MySQL with my desktop user and no-password (hence, access denied)

the changes just not stored by amarok, how to solve this?

---

