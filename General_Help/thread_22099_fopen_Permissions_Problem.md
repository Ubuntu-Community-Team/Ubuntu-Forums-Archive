---
title: "fopen Permissions Problem"
date: 2005-03-25
forum: General Help
---

### Post by iso on 2005-03-25
I'm having some problems with apache not being able to write files.  The following is some php code that creates and writes some data to a file.  However, when i run it, i get the following error.

```

<?
$fp = fopen("my.log","a");
$str = date("Y-m-d H:i:s") . ".  code : " .$error_code . "." ;
fwrite ($fp,$str . "\r\n");
 fclose($fp);
?>

``` 

Warning: fopen(my.log): failed to open stream: No such file or directory in /var/www/www.fightemo.com/htdocs/write.php on line 2

Warning: fwrite(): supplied argument is not a valid stream resource in /var/www/www.fightemo.com/htdocs/write.php on line 4

Warning: fclose(): supplied argument is not a valid stream resource in /var/www/www.fightemo.com/htdocs/write.php on line 5


```
root@dante:/var/www/www.fightemo.com/htdocs # ls -la
drwxrwxrwx 8 www-data www-data     4096 2005-03-25 15:53 .
drwxr-xr-x    5 root      www-data     4096 2005-03-24 08:57 ..
drwxrwxr-x   2 emo      www-data     4096 2004-08-03 23:31 admin
-rw-rwxr--    1 emo      www-data     1785 2004-07-13 18:27 base.css
-rw-rwx---    1 emo      www-data      181 2004-08-04 00:08 .bash_history
-rwxrwxrwx  1 emo	    www-data      139 2005-03-25 15:53 write.php
-rw-rwxr--     1 emo      www-data       15 2004-07-11 16:19 xhtmlFoot.php
-rw-rwxr--     1 emo      www-data      482 2004-07-29 15:50 xhtmlHead.php

root@dante:/var/www/www.fightemo.com # ls -la
total 24
drwxr-xr-x     5 root     www-data     4096 2005-03-24 08:57 .
drwxr-xr-x   22 root     www-data     4096 2005-03-10 15:19 ..
drwxrwxrwx  8 www-data www-data     4096 2005-03-25 15:53 htdocs
-rw-r-xr--       1 emo       www-data       18 2004-08-03 23:29 .htpasswd
drwxr-xr-x     2 root      www-data     4096 2005-01-11 21:25 logs
drwxrwxrwx   4 emo       www-data     4096 2005-03-24 10:31 PEAR

``` 

```

root@dante:/var/www/www.fightemo.com # ps -Af |grep apache
root     11772     1  0 Mar23 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data 11777 11772  0 Mar23 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data 19916 11772  0 12:54 ?        00:00:03 /usr/sbin/apache2 -k start -DSSL
www-data 20458 11772  0 13:42 ?        00:00:02 /usr/sbin/apache2 -k start -DSSL
www-data 20493 11772  0 13:42 ?        00:00:02 /usr/sbin/apache2 -k start -DSSL
www-data 20796 11772  0 14:10 ?        00:00:01 /usr/sbin/apache2 -k start -DSSL
www-data 20898 11772  0 14:21 ?        00:00:01 /usr/sbin/apache2 -k start -DSSL
www-data 21000 11772  0 14:29 ?        00:00:01 /usr/sbin/apache2 -k start -DSSL
www-data 21004 11772  0 14:29 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data 21234 11772  0 14:35 ?        00:00:01 /usr/sbin/apache2 -k start -DSSL
www-data 22079 11772  0 16:03 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data 22121 11772  0 16:08 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
root     22307  2980  0 16:29 pts/2    00:00:00 grep apache


``` 



Linux dante 2.6.8.1-5-686-smp #1 SMP Mon Mar 14 21:59:14 UTC 2005 i686 GNU/Linux

---

### Post by DJ_Max on 2005-03-25
You need the proper permissions to write in /var

---

### Post by iso on 2005-03-27
i chmoded /var/ recursively for group - read, write, execute and changed the group to www-data.  This however did not solve the problem.

---

### Post by iso on 2005-03-28
Still having this problems. I was able to rule out a few things.  Am i overlooking something?

open_basedir is not specified
php is not running in safe-mode

drwxrwxrwx   15 www-data www-data     4096 2005-03-20 15:14 var
drwxrwxrwx    5 www-data www-data     4096 2005-03-23 02:12 www

groups www-data 
www-data : www-data

---

### Post by DJ_Max on 2005-03-28
oh, instead of chmoded /var/, why not use your home directory.  Put everything in /home/<username>/public_html
It's safer, then you access it as http://localhost/~<username>

---

### Post by iso on 2005-04-02
I have multiple v-hosts set up and everything is situated in /var/www/ 
I have tried using the full path in the code and I still receive the same error.

---

### Post by iso on 2005-04-07
Updated the kernel.  Problem went away.

apt-get install linux-686-smp

Thx all for looking.  \\:D/

---

