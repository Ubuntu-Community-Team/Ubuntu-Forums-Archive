---
title: "WordPress 1.5 error"
date: 2005-04-09
forum: General Help
---

### Post by macewan on 2005-04-09
Your PHP installation appears to be missing the MySQL which is required for WordPress.

everything is installed - suggestions?

---

### Post by DJ_Max on 2005-04-09
You do have MySQL & the php4-mysql packages installed?

---

### Post by macewan on 2005-04-09
yes

---

### Post by macewan on 2005-04-10
ok, WordPress is saying that mysql module isn't loading. it's being tested in wp-settings.php on line 19

```
if ( !extension_loaded('mysql') )
	die( 'Your PHP installation appears to be missing the MySQL which is required for WordPress.' );
```

OK - so I'm starting from the beginning and removing all LAMP and then do


sudo apt-get install apache2 mysql-server php4

sudo vi +536 /etc/php4/apache2/php.ini

remove **;** from in front of extension=mysql.so

sudo apt-get install phpmyadmin

it works now

If you're still having problems with local install of WordPress 1.5 on Hoary you could always just comment out the mysql test

sudo vi +19 /var/www/wordpress/wp-settings.php

comment out the module test here

---

