---
title: "uninstall reinstall mysql"
date: 2007-05-18
forum: General Help
---

### Post by fastfinger on 2007-05-18
i accidently deleted 'root' in my mysql and i cant seem to fix it and i tried to uninstall and/or reinstall mysql but i cant seem to do that either apt-get says 
:Package mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
confused:

---

### Post by spin2cool on 2007-05-18
IIRC, there is no 'mysql' package.  You'll want to try one or more of the following:

mysql-client
mysql-common
mysql-server
libmysqlclient12
libqt3c102-mt-mysql
libdbd-mysql-perl
php4-mysql

Also, remember that you can search Synaptic package manager for the keyword 'mysql' and pull up a list of exactly what is installed.

---

### Post by fastfinger on 2007-05-18
ok, i was able to remove and reinstall
apt-get remove mysql-server -y
apt-get install mysql-server -y

but i still get 
Warning: mysql_connect(): Access denied for user 'root'@'localhost' (using password: NO)

i tried this
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)
but i couldnt make it work. In the alternative method, i did 
kill `cat mysqld.pid` and did what that link said but it said 
another instant of mysqld might be running so i was unable to do that to.

---

