---
title: "can't insert table in MySQL"
date: 2014-12-27
forum: General Help
---

### Post by johnnybgoode on 2014-12-27
i alway receive the "Can't get stat..." message. See snippet 
                        mysql> load data infile "abc.txt" into table book; 
 ERROR 13 (HY000): Can't get stat of '/var/lib/mysql/cd/abc.txt' (Errcode: 2) 
 mysql>  
                                                              where is that "cd" coming from?
Database name is: cd
 Table name = book
 

 root@john-Aspire-M3300:/var/lib/mysql# ls 
 abc.txt   cd      ib_logfile0  mysql_upgrade_info 
 boeken   debian-5.5.flag  ib_logfile1  performance_schema 
 book     ibdata1          mysql

---

### Post by The Cog on 2014-12-27
My guess is that cd has been set as your default database. If the file is elsewhere, then I guess you need to give the full path.

Bear in mind that the server accepts this command and looks in the **server's filesystem** for abc.txt. You cannot load files remotely (i.e. from the filesystem of a client PC) this way.

---

### Post by johnnybgoode on 2014-12-31
SOLVED    Thank you. I was making a path mistake!

---

