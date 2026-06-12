---
title: "apache2 downloading php files instead of displaying it"
date: 2014-06-20
forum: General Help
---

### Post by garo2 on 2014-06-20
Hello,
when i open any php file the browser prompt me to download it rather that display it and when i open the info.php file it opens normally. i've tried every solution i found here for this problem but none of them work ..
so any help?

---

### Post by yancek on 2014-06-20
Did you read the php.info output?  If you don't understand it, you could post it for someone else to review.  Delete the History on the browser.  By the way, it might help if you indicated which browser you are using.  You would have to give some detail on what 'every solution' means since we don't know what you have done.  Probably mis-configured httpd file or maybe php.ini.

---

### Post by thnewguy on 2014-06-20
You probably need to change Apache's PHP configuration. Check out this page for details: [https://pricklytech.wordpress.com/2011/04/02/ubuntu-server-apache-php-files-are-download-instead-of-opening-in-browser/](https://pricklytech.wordpress.com/2011/04/02/ubuntu-server-apache-php-files-are-download-instead-of-opening-in-browser/)

---

### Post by garo2 on 2014-06-20
i'm using mozilla, and i have tried to do what i found here [http://ubuntuforums.org/showthread.php?t=1361019](http://ubuntuforums.org/showthread.php?t=1361019)
and the apache's PHP configuration is right

---

### Post by SeijiSensei on 2014-06-20
Is info.php in /var/www or /var/www/html, but the files that don't work in some other directory?  If you're using Apache's Userdir feature, read [this thread](http://ubuntuforums.org/showthread.php?t=2230036).

---

### Post by garo2 on 2014-06-20
info.php is in /var/www/html same as the other files and i commented the <directory>container lines

---

### Post by SeijiSensei on 2014-06-20
What do you see in /var/log/apache2/access.log and /var/log/apache2/error.log when you try and open the inoperative files?

---

### Post by garo2 on 2014-06-20
access.log
```
127.0.0.1 - - [21/Jun/2014:23:33:43 +0200] "GET / HTTP/1.1" 200 3594 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [21/Jun/2014:23:33:43 +0200] "GET /icons/ubuntu-logo.png HTTP/1.1" 200 3688 "http://localhost/" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [21/Jun/2014:23:33:44 +0200] "GET /favicon.ico HTTP/1.1" 404 498 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
1.0.0.17 - - [21/Jun/2014:23:47:07 +0200] "GET / HTTP/1.1" 200 3594 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
1.0.0.17 - - [21/Jun/2014:23:47:07 +0200] "GET /icons/ubuntu-logo.png HTTP/1.1" 200 3688 "http://1.0.0.17/" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
1.0.0.17 - - [21/Jun/2014:23:47:07 +0200] "GET /favicon.ico HTTP/1.1" 404 497 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
1.0.0.17 - - [21/Jun/2014:23:47:07 +0200] "GET /favicon.ico HTTP/1.1" 404 497 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
1.0.0.17 - - [21/Jun/2014:23:47:26 +0200] "GET /info.php HTTP/1.1" 200 18169 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:00:02:49 +0200] "GET / HTTP/1.1" 200 3594 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:00:02:49 +0200] "GET /icons/ubuntu-logo.png HTTP/1.1" 200 3688 "http://localhost/" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:00:22:46 +0200] "GET /test.php HTTP/1.1" 404 496 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:00:23:30 +0200] "GET /info.php HTTP/1.1" 200 18181 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:00:25:20 +0200] "GET /test.php HTTP/1.1" 200 18183 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:03:00:35 +0200] "GET /php.info HTTP/1.1" 404 496 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:03:00:41 +0200] "GET /php.info HTTP/1.1" 404 496 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:03:00:46 +0200] "GET / HTTP/1.1" 200 3594 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:03:00:46 +0200] "GET /icons/ubuntu-logo.png HTTP/1.1" 200 3688 "http://localhost/" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:03:00:56 +0200] "GET /test.php HTTP/1.1" 200 18169 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"
127.0.0.1 - - [22/Jun/2014:03:33:22 +0200] "GET / HTTP/1.1" 200 3594 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0"

```
error.log
```

[Sat Jun 21 23:33:12.886609 2014] [mpm_event:notice] [pid 10406:tid 140231244326784] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Sat Jun 21 23:33:12.886749 2014] [core:notice] [pid 10406:tid 140231244326784] AH00094: Command line: '/usr/sbin/apache2'
[Sat Jun 21 23:42:08.170286 2014] [mpm_event:notice] [pid 10406:tid 140231244326784] AH00491: caught SIGTERM, shutting down
[Sat Jun 21 23:42:09.260222 2014] [mpm_prefork:notice] [pid 17247] AH00163: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Sat Jun 21 23:42:09.260344 2014] [core:notice] [pid 17247] AH00094: Command line: '/usr/sbin/apache2'
[Sat Jun 21 23:42:09.603551 2014] [mpm_prefork:notice] [pid 17247] AH00169: caught SIGTERM, shutting down
[Sat Jun 21 23:42:10.744341 2014] [mpm_prefork:notice] [pid 17331] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Sat Jun 21 23:42:10.744413 2014] [core:notice] [pid 17331] AH00094: Command line: '/usr/sbin/apache2'
[Sat Jun 21 23:45:28.894547 2014] [mpm_prefork:notice] [pid 17331] AH00169: caught SIGTERM, shutting down
[Sat Jun 21 23:45:30.011294 2014] [mpm_prefork:notice] [pid 17544] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Sat Jun 21 23:45:30.011367 2014] [core:notice] [pid 17544] AH00094: Command line: '/usr/sbin/apache2'
[Sat Jun 21 23:54:23.647036 2014] [mpm_prefork:notice] [pid 17544] AH00169: caught SIGTERM, shutting down
[Sat Jun 21 23:54:24.765697 2014] [mpm_prefork:notice] [pid 18028] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Sat Jun 21 23:54:24.765770 2014] [core:notice] [pid 18028] AH00094: Command line: '/usr/sbin/apache2'
[Sun Jun 22 00:16:14.083814 2014] [mpm_prefork:notice] [pid 18028] AH00169: caught SIGTERM, shutting down
[Sun Jun 22 00:16:15.207793 2014] [mpm_prefork:notice] [pid 19279] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Sun Jun 22 00:16:15.207865 2014] [core:notice] [pid 19279] AH00094: Command line: '/usr/sbin/apache2'
[Sun Jun 22 00:18:21.802016 2014] [mpm_prefork:notice] [pid 19279] AH00169: caught SIGTERM, shutting down
[Sun Jun 22 00:18:22.925299 2014] [mpm_prefork:notice] [pid 19431] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Sun Jun 22 00:18:22.925375 2014] [core:notice] [pid 19431] AH00094: Command line: '/usr/sbin/apache2'
[Sun Jun 22 00:22:46.965468 2014] [:error] [pid 19435] [client 127.0.0.1:49553] script '/var/www/html/test.php' not found or unable to stat
[Sun Jun 22 00:49:07.480649 2014] [mpm_prefork:notice] [pid 19431] AH00169: caught SIGTERM, shutting down
[Sun Jun 22 00:49:08.595583 2014] [mpm_prefork:notice] [pid 20942] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Sun Jun 22 00:49:08.595657 2014] [core:notice] [pid 20942] AH00094: Command line: '/usr/sbin/apache2'
[Sun Jun 22 03:33:34.319584 2014] [mpm_prefork:notice] [pid 20942] AH00169: caught SIGTERM, shutting down
[Sun Jun 22 03:33:35.434427 2014] [mpm_prefork:notice] [pid 28503] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Sun Jun 22 03:33:35.434502 2014] [core:notice] [pid 28503] AH00094: Command line: '/usr/sbin/apache2'
```

---

### Post by lisati on 2014-06-20
You might need to (re)install libapache2-mod-php5. 

Source: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5)

---

### Post by garo2 on 2014-06-20
i purge libapache2-mod-php5 and reinstall it again and cleared browser cashe and still prompt me to download

---

