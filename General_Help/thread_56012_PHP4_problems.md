---
title: "PHP4 problems"
date: 2005-08-11
forum: General Help
---

### Post by kg6gfq on 2005-08-11
I've been trying to install [Drupal](http://drupal.org)  4.6.2 on a P3 with Ubuntu Hoary.  I've fiddled with Apache, PHP, and MySQL configurations and reinstalled various versions completely.  I've also tried installing Drupal from Synaptic, but that doesn't seem to do anything and my attempts to install it by hand keep having another problem - when I go to [http://localhost/](http://localhost/) or [http://localhost/index.php](http://localhost/index.php) (it's installed in the root directory of the server) Firefox tries to download index.php, instead of displaying it.  I would guess that it is a problem with Apache or PHP configuration, but I don't know enough about either to say for sure.  I've been doing the configuration of the servers through Webmin, and fiddling with some settings there, but again I don't know enough about what I'm doing.  

Any suggestions would be appreciated!  Thanks in advance!!

-Darin Wick
      Have a nice day!

---

### Post by mrcbrown on 2005-08-11
[QUOTE=kg6gfq]I've been trying to install [Drupal](http://drupal.org)  4.6.2 on a P3 with Ubuntu Hoary.  I've fiddled with Apache, PHP, and MySQL configurations and reinstalled various versions completely.  I've also tried installing Drupal from Synaptic, but that doesn't seem to do anything and my attempts to install it by hand keep having another problem - when I go to [http://localhost/](http://localhost/) or [http://localhost/index.php](http://localhost/index.php) (it's installed in the root directory of the server) Firefox tries to download index.php, instead of displaying it.  I would guess that it is a problem with Apache or PHP configuration, but I don't know enough about either to say for sure.  I've been doing the configuration of the servers through Webmin, and fiddling with some settings there, but again I don't know enough about what I'm doing.  

Any suggestions would be appreciated!  Thanks in advance!!

-Darin Wick
      Have a nice day![/QUOTE]
 How did you install php/apache? Synaptic? 

I ended up compiling everything short of SQL's from source, let me configure a bit more what things php did / didn't support - as I wanted GD support and a few other tiny tweaks for some apps I am writing.

---

### Post by kg6gfq on 2005-08-11
[QUOTE=mrcbrown]How did you install php/apache? Synaptic? [/QUOTE]

I used Synaptic.  Thanks for the tip about compiling from source, I'll try it.

---

### Post by mrcbrown on 2005-08-11
[QUOTE=kg6gfq]I used Synaptic.  Thanks for the tip about compiling from source, I'll try it.[/QUOTE]
 If you need help feel free to drop me a PM - glad to throw in two bits if ya need help, and I can definately help tweak php.ini/apache.conf if needed.

---

### Post by mksoft on 2005-08-11
Looks like you didn't enable php in apache configs.

You should symlink (or copy) php4.conf and php4.load from /etc/apache2/mods-available/ to /etc/apache2/mods-enabled/ and restart apache.

---

### Post by kg6gfq on 2005-08-11
I reinstalled Ubuntu and with some work got everything set up. I compiled both Apache and PHP5 (I was using PHP4 before). MySQL I installed using Ubuntu's package repositories and Synaptic. After following the directions at [http://www.php.net/manual/en/install.unix.apache2.php](http://www.php.net/manual/en/install.unix.apache2.php) and those in the Drupal handbook I got it up and running. (Though not without fixing dependencies and adjusting httpd.conf to look for index.php as an index file.)

Thanks to all of you for your suggestions and those I got at [the Drupal Forums](http://drupal.org/node/28664)!

-Darin Wick
Have a nice day!

---

