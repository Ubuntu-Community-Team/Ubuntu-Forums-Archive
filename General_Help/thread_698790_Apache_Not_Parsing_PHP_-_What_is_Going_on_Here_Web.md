---
title: "Apache Not Parsing PHP - What is Going on Here? Webmin PHP configuration help?"
date: 2008-02-16
forum: General Help
---

### Post by wilshire on 2008-02-16
I've read the others threads on this. Done everything they say. I'm at my wits end.

When I try to open a .php file residing on my server from firefox, firefox asks me if i'd like to download the file. apache is not parsing it as it should. 

PHP is installed and loaded:

Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at 127.0.0.1 Port 80

and

jim@jim-desktop:~$ sudo a2enmod php5
[sudo] password for jim:
This module is already enabled!



/etc/apache2/apache2.conf includes the lines:

AddType application/x-httpd-php .php .phtml
Include /etc/phpmyadmin/apache.conf



symlinks to php.conf and php.load are present under /etc/apache2/mods-enabled

php.conf reads:

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

the package libapache2-mod-php5 is installed.


So what is going on here?

one thing i should say is that i have webmin installed, and it has a module for PHP configuration. the module asks for input for: 

"PHP Admin Configuration Values", "PHP Configuration Values", "PHP Admin Configuration Flags", and "PHP Configuration Flags". I don't have anything filled in because i don't know what it's asking. might that be the issue? what do you think it's asking for?

---

### Post by wilshire on 2008-02-16
uninstalling and then reinstalling 'fixed' the problem. i guess i'll never know what the real problem is.

---

