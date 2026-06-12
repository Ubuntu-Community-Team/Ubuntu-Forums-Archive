---
title: "Apache 2 and PHP 4"
date: 2004-11-02
forum: General Help
---

### Post by gasky on 2004-11-02
I've installed Apache 2 and libapache2-mod-php4. Apache is up and running but everytime I try to access a .php page I get a box that asks me if i want to save the file to disk or choose which application I want to open it with. In my etc/apache2/mods-available directory I have both php4.conf and php4.load files.
php4.conf reads:
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

php4.load reads:
LoadModule php4_module /usr/lib/apache2/modules/libphp4.so

Both files are also in etc/apache2/mods-enabled directory. Any ideas why Apache is not processing .php files?
Thanks.

---

### Post by p__wack on 2004-11-02
[QUOTE=gasky]I've installed Apache 2 and libapache2-mod-php4. Apache is up and running but everytime I try to access a .php page I get a box that asks me if i want to save the file to disk or choose which application I want to open it with. In my etc/apache2/mods-available directory I have both php4.conf and php4.load files.
php4.conf reads:
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

php4.load reads:
LoadModule php4_module /usr/lib/apache2/modules/libphp4.so

Both files are also in etc/apache2/mods-enabled directory. Any ideas why Apache is not processing .php files?
Thanks.[/QUOTE]
 check the config of the file extesions for PHP files, in one server I have troubles running php3 files.
 try it!

bye

---

### Post by diebels on 2004-11-02
I had the same problem, doing /etc/init.d/apache2 stop and /etc/init.d/apache2 start fixed it. Seems like it got started before mod-php was installed.

---

