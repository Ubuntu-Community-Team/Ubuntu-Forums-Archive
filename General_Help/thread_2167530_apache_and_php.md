---
title: "apache and php"
date: 2013-08-14
forum: General Help
---

### Post by human2 on 2013-08-14
Php do not work in apache

I have install nginx and apache on Ubuntu. 

My steps
1. sudo apt-get install apache2
2. sudo apt-get install php5 php5-cli php5-dev php5-common php5-fpm php5-gd php5-mcrypt php5-memcache php5-memcached php5-mysql
3. sudo apt-get install libapache2-mod-php5
4. sudo /etc/init.d/apache2 restart

5.
I change following line in **/etc/apache2/ports.conf**
**Listen 80 -> Listen 8080**

6. sudo /etc/init.d/apache2 restart

7. add ```
<?php  phpinfo();  ?>
``` code to** /var/www/index.html** file

8. run in firefox [http://localhost:8080/](http://localhost:8080/) 

look at next text:
```
**It works!**

 This is the default web page for this server.

 The web server software is running but no content has been added, yet.
```



I don't see info about php. Php code is ignored.

On this moment google not helped

---

### Post by cLfsdE4 on 2013-08-14
Create info.php in www directory and in info.php paste this php code. It may work ;)

---

### Post by human2 on 2013-08-14
[http://localhost:8080/info.php](http://localhost:8080/info.php)   yes it working

---

