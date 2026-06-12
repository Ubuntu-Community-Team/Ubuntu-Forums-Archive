---
title: "mysql and locked priviledge tables"
date: 2007-07-17
forum: General Help
---

### Post by bjdekruif on 2007-07-17
Hello all, 

While I was booting, my system completely froze. Although this freezing is likely to be connected to my videocard, since it didn't happen now that I changed it, my mysql database won't start anymore.

The error I get in my syslog is:
 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'host'

Does anybody know what this error means, and how I can correct it?

I found out that my backup script didn't work as it should, something you only check if it is too late, so any help would be greatly appreciated. 

If I cannot correct the above error, is it possible to start with a new database on some new location and copy the files? The database is used for Mythtv, if it might be of any influence.

Thanks for all help 

yours

bas

-----new info

If I start with sudo mysqld --skip-grant-tables then the system will start. But if I repair it with mysqlcheck -r -u root mythconverg, nothing is solved the next time I want to start it (without the --skip-grant-tables)

---

### Post by pleira on 2007-07-19
You can reconstruct the main tables host, user and db. First:

web:~# cd /var/lib/mysql/mysql
web:/var/lib/mysql/mysql# rm host*
web:/var/lib/mysql/mysql# rm user*
web:/var/lib/mysql/mysql# rm db*

Then

web:/var/lib/mysql/mysql# mysql_install_db

---

