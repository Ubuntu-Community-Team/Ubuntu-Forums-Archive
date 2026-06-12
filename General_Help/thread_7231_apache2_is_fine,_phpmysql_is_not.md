---
title: "apache2 is fine, php/mysql is not"
date: 2004-12-05
forum: General Help
---

### Post by wiseNoob on 2004-12-05
I followed the directions here:
[http://www.myjavaserver.com/~mike001/ubuntu/#installapachehttpserver](http://www.myjavaserver.com/~mike001/ubuntu/#installapachehttpserver)

phpinfo.php returned correctly and then,

mysql gave me an error:
> mysqladmin /usr/bin/mysqladmin -u root password password-here
> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

so... I thought I installed in the wrong order or something - removed:
mysql-server
libapache2-mod-auth-mysql
php4-mysql
php4
libapache2-mod-php4
-- in that order.

reinstalled:
php4
libapache2-mod-php4

php is not working now.  any thoughts?  :mad:

---

### Post by jiyuu0 on 2004-12-05
did u use sudo

$ sudo /usr/bin/mysqladmin -u root password your_root_user_password

---

### Post by wiseNoob on 2004-12-05
Actually I was logged in as root.  Didn't think I could apt-get unless I was sudo or root -

---

### Post by firfin on 2005-02-28
[QUOTE=jiyuu0]did u use sudo

$ sudo /usr/bin/mysqladmin -u root password your_root_user_password[/QUOTE]
 I did use sudo but i get the same msg. Does anyon ehave an idea what's happening. 
Here's what I did and the repsonse.
> firfin@morpheus:/opt/ariadne/files $ sudo /usr/bin/mysqladmin -u root password xxxxxxxx
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

---

### Post by natefish on 2005-03-02
WiseNoob did you ever get the php too work after it stopped? I am having the same problem, I tried restart of server etc. Just stopped working after reinstall.

---

### Post by hantsy on 2005-03-02
[QUOTE=wiseNoob]I followed the directions here:
[http://www.myjavaserver.com/~mike001/ubuntu/#installapachehttpserver](http://www.myjavaserver.com/~mike001/ubuntu/#installapachehttpserver)

phpinfo.php returned correctly and then,

mysql gave me an error:
> mysqladmin /usr/bin/mysqladmin -u root password password-here
> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

so... I thought I installed in the wrong order or something - removed:
mysql-server
libapache2-mod-auth-mysql
php4-mysql
php4
libapache2-mod-php4
-- in that order.

reinstalled:
php4
libapache2-mod-php4

php is not working now.  any thoughts?  :mad:[/QUOTE]
 Mysql client is requried
Php4 mod must be activated before using...

---

