---
title: "MySQL 5.0 Server Problem"
date: 2007-02-21
forum: General Help
---

### Post by silverbolt027 on 2007-02-21
I am attempting to setup mysql for Ubuntu 6.10 edgy so that I can use MythTV...but I am running into to some issues.  When I first attempted to start the mysql service, it gave me the following error in my syslog:

/etc/init.d/mysql[7591]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)'
/etc/init.d/mysql[7591]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

The file doesn't even exist.  So I downloaded the newer version from the mysql.com website, installed the binary, and presto I could run the server, create databases/tables, etc.  The problem was that when I tried to install mythtv it would reference the older (pre-installed version) of mysql and not the one I had setup.

So I have attempted to go back to the pre-installed version, changing the my.cnf around, disabling innodb, changing the bind-address...anything and everything I can find.

Can anyone give me some help on where to start?  Or help me diagnose this problem?? 

Thanks in advance!

---

### Post by der_joachim on 2007-02-21
[This Wiki]("https://help.ubuntu.com/community/ApacheMySQLPHP") page may help you further. Look for the part about MySQL.

---

### Post by silverbolt027 on 2007-02-21
Thanks for the info...but I actually just removed the my.cnf file, and then ran sudo apt-get install mysql-server again and everything installed and is working just fine now.

Thanks!

---

