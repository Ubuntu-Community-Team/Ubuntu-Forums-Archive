---
title: "Apache and php issue"
date: 2012-12-13
forum: General Help
---

### Post by miles95 on 2012-12-13
I'm trying to run php files and instead they just download. 
this is my httpd conf file. i've been searching for 3 days for a fix and nothing is working for me any help would be great. i'm running 12.04 


ServerName localhost
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

This is what i get when i restart. 
[Thu Dec 13 14:04:42 2012] [warn] module php5_module is already loaded, skipping
 ... waiting [Thu Dec 13 14:04:43 2012] [warn] module php5_module is already loaded, skipping
                                                                                 [ OK ]

---

