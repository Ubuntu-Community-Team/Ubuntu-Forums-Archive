---
title: "mysql lost contact with  joomla data base"
date: 2014-08-04
forum: General Help
---

### Post by n41076jem-2 on 2014-08-04
First I do not have a backup of the joomla data base, yes I am VERY bad.

-------------------------------------

System upgrade to trusty, all was well.
Web ran well  fine,  system was reboot  and  joomla lost contact with mysql.

--------------------------------------


long story short end up reinstalling mysql 5.5 and phpmyadmin. The production database is all there. 

is there a way to get mysql working with it again

---

### Post by n41076jem-2 on 2014-08-04
Is there a tool that can take the production database and do an export? So it can be re imported?

---

### Post by n41076jem-2 on 2014-08-04
Again a long story short,


Why I re-installed mysql,  after the reboot mysqld would not start. 
 I tried  myisamchk --silent --force */*.MYI and well still would not start.


I completely purged mysql-server 5.5 and then installed it
My production DB is there but mysql does not see it

---

