---
title: "Mysql Error 2002"
date: 2007-03-30
forum: General Help
---

### Post by Aurdal on 2007-03-30
Mysql reports the following error when I try to start it:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

mysqld returns:

070330 19:04:25 [ERROR] Fatal error: Can't change to run as user 'mysql' ;  Please check that the user exists!

070330 19:04:25 [ERROR] Aborting

070330 19:04:25 [Note] mysqld: Shutdown complete

------------------------------------------------------------------

Any suggestions?

---

### Post by phidia on 2007-03-30
This sounds like a permissions issue.

> check that the user you set mysql to run as exists and that it has the necessary permisions over the file and the directory structure it lies under.

let's say that mysql holds its databases in /usr/local/share/mysqldata and that it was set to run as mysql

# grep mysql /etc/passwd

if the user is not there, create the group for it, say mysql with gid 55 (let's say)

# adduser -s /sbin/nologin -m -g mysql mysql
# chown -v -R /usr/local/share/mysqldata
# chgrp -v -R /usr/local/share/mysqldata
# chmod -v -R 644 /usr/local/share/mysqldata

now mysql should have all the permissions it requires

---

### Post by Aurdal on 2007-03-30
Thank you for replying so fast.

The problem persists though, none of those commands worked.

---

### Post by phidia on 2007-03-30
I'm not a mysql expert. It's just a thought but you might want to check out the forum(s) specific to mysql.

[http://www.analysisandsolutions.com/code/mybasic.htm](http://www.analysisandsolutions.com/code/mybasic.htm)

[http://www.php-editors.com/forums/forumdisplay.php?f=20](http://www.php-editors.com/forums/forumdisplay.php?f=20)

[http://www.devshed.com/c/b/MySQL/](http://www.devshed.com/c/b/MySQL/)

---

