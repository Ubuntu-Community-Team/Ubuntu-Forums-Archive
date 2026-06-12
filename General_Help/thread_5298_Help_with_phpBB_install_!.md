---
title: "Help with phpBB install !"
date: 2004-11-17
forum: General Help
---

### Post by fdimeglio on 2004-11-17
Hi,

I just want to install and run phpBB. I have done the following package installs and configurations with Synaptics (no problem reported):

- mysql-common
- mysql-server
- mysql-client
- php4
- php4-cgi
- php-mysql
- phpmyadmin
- phpbb2
- phpbb2-conf-mysql

phpmyadmin is working correctly and I can access it thru [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

phpbb2-conf-mysql should have configured a mySQL database for phpBB2 but looking at the databases I cannot see any except the "test" one.

[http://localhost/phpbb](http://localhost/phpbb) gives nothing.


Any clues about this problem ?


Fabrice

---

### Post by sfw5000 on 2004-11-17
Usually you configure phpBB2 by going using the install script. I think it's either localhost/phpBB2/install.php or /admin/install.php -- that creates the data base and everything for you.

---

