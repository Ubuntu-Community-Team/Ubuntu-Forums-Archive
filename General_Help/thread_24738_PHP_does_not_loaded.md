---
title: "PHP does not loaded?"
date: 2005-04-08
forum: General Help
---

### Post by vitti on 2005-04-08
Hallo!
Now I have installed apaceh2, php4, webmin & more. :wink: 
Apache is working, but if I try to open a page containg a php file I got an error like the attach! ](*,) 
How may I sure that php is loaded and running?
Thanks!

---

### Post by sas on 2005-04-08
Are you opening the file by going to [http://localhost/header.php](http://localhost/header.php) ?
Can you check that mod_php is installed?

What's happening is that apache isn't realising it's supposed to be executing the file, you might want to search for information about apache mime types or something...

---

### Post by orion_114 on 2005-04-08
You need to edit your apache2.conf file and uncomment the lines
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

This should solve your problem.
I cant think offhand where the file resides (On winXp now) so just do a file search.

---

### Post by magnet on 2005-04-08
Sorry this is not for this place.

Hello, sorry for may English.

I have a litel problem. I need install the additional .ini files parsed. 
I install with Synaptic de apache2 and modules for Php and sql. And all is working, thw web, de php, but phpmyadmin say this:

[I] [1.20] I receive the error "cannot load MySQL extension, please check PHP Configuration".

To connect to a MySQL server, PHP needs a set of MySQL functions called "MySQL extension". This extension may be part of the PHP distribution (compiled-in), otherwise it needs to be loaded dynamically. Its name is probably mysql.so or php_mysql.dll. phpMyAdmin tried to load the extension but failed.

Usually, the problem is solved by installing a software package called "PHP-MySQL" or something simila[/I]

idon't now who install this extension.


thank's a lot

---

### Post by bmichel on 2005-04-08
[QUOTE=magnet]Sorry this is not for this place.

Hello, sorry for may English.

I have a litel problem. I need install the additional .ini files parsed. 
I install with Synaptic de apache2 and modules for Php and sql. And all is working, thw web, de php, but phpmyadmin say this:

[I] [1.20] I receive the error "cannot load MySQL extension, please check PHP Configuration".

To connect to a MySQL server, PHP needs a set of MySQL functions called "MySQL extension". This extension may be part of the PHP distribution (compiled-in), otherwise it needs to be loaded dynamically. Its name is probably mysql.so or php_mysql.dll. phpMyAdmin tried to load the extension but failed.

Usually, the problem is solved by installing a software package called "PHP-MySQL" or something simila[/I]

idon't now who install this extension.


thank's a lot[/QUOTE]
 you have a file named php.ini  in /etc/php4/apache2 

search for keyword extension

you should have something like ;extension=mysql.so 

so remove ; and mysql will be activated (perhaps you must restart apache2: apache2ctl restart)

---

### Post by macewan on 2005-04-10
sudo apt-get install phpmyadmin

I had this problem with a local copy of WordPress 1.5 on Hoary.

---

