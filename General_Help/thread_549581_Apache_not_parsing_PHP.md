---
title: "Apache not parsing PHP"
date: 2007-09-12
forum: General Help
---

### Post by skunkwerk on 2007-09-12
I have tried using the guide here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
but when I go to firefox and type in localhost/test.php, it prompts me to download the file

i've uncommented this line in /etc/apache2/apache2.conf:
#AddType application/x-httpd-php .php

sudo a2enmod php5 yields:
This module is already enabled!

i have tried restarting apache and my server, doesn't make a difference
libapache2-mod-php5 is installed

thanks

---

### Post by aot2002 on 2007-09-12
try this 
sudo dpkg-reconfigure apache

---

### Post by skunkwerk on 2007-09-12
thanks, but that didn't work.  i did notice that php5 wasn't in the list of modules it asked me  to load, though.

---

### Post by aot2002 on 2007-09-13
ok if php is not in the modules then check your httpd.conf and make sure you really are loading this line

here is the line

LoadModule php5_module modules/libphp5.so

is it uncommented in your file?

---

### Post by Nesman on 2007-09-13
I also had trouble getting php to work.  I ended up using Xampp from [http://apachefriends.org](http://apachefriends.org) and it worked like a charm.  Please note that they do not suggest that you use Xampp in a production enviroment.  Also, the install is too easy, so you don't really learn anything. :P

---

### Post by aot2002 on 2007-09-13
yea but the nice thing about xampp is that its confined into one directory mine is in /opt/lammp

so if i upgrade i can just backup that directory and reinstall quicker.

---

### Post by skunkwerk on 2007-09-14
it doesn't exist in my httpd.conf for apache or apache2
i added it to /etc/apache2/httpd.conf but it didn't change anything

---

### Post by skunkwerk on 2007-09-14
i just reinstalled with ubuntu server, works like a charm now

thanks

---

### Post by lobo-tuerto on 2008-01-16
But what happened??

I'm having the same problem, everything is configured, no errors in the log, php installed, and still Apache2 isn't parsing my php files :(

I'm using Ubuntu 7.10 Gutsy Gibbon.

---

### Post by danwood76 on 2008-01-16
whenever I have installed a PHP/Apache/MySQL server I have installed all three from the same apt-get line and they normally setup and work perfectly without modification.

If you can try completely removing apache and php with synaptic and re installing to see if it helps.

regards,
Danny

---

### Post by lobo-tuerto on 2008-01-16
Thanks ;)

---

