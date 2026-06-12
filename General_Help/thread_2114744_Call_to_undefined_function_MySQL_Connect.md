---
title: "Call to undefined function MySQL_Connect"
date: 2013-02-10
forum: General Help
---

### Post by yeikel on 2013-02-10
Hi guys :popcorn: 

My day has been a disaster thanks to apache issues :guitar: 

After [this topic]("http://ubuntuforums.org/showthread.php?p=12503284")  , now I am into a new problem : MySQL_Connect does not work :lolflag:
I know that php5-mysql is needed so that is one of the things that I have installed but when I run my script I got : 

>  Fatal error:  Call to undefined function mysql_connect() in /var/www/test.php on line 2Script :

[PHP]<?php
mysql_connect("localhost", "root", "mypassword") or die(mysql_error());
echo "Connected to MySQL<br />";
?>[/PHP]What I have installed(in order)

```
apt-get install apache2
apt-get install mysql-server
apt-get install php5
apt-get install php5-mysql
```


Any idea? :KS

---

### Post by cthugha on 2013-02-10
Did you restart apache after installing php5-mysql?

---

### Post by yeikel on 2013-02-10
> **cthugha said:**
> Did you restart apache after installing php5-mysql?
Yes of course :confused::confused:

---

### Post by cthugha on 2013-02-10
Make a page with <?php phpinfo(); exit(); ?> and see if you can find MySQL anywhere.

Have you tried installing everything using taksel? It's pretty simple to just install the LAMP stack, and it comes with everything you'd want pre-configured to work well with each other. [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

