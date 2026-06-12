---
title: "2 sites on Apache 2, one runs php, one doesn't."
date: 2007-12-07
forum: General Help
---

### Post by qwert231 on 2007-12-07
Ubuntu 7.04, Apache2, and PHP 5 are all loaded. you can see that it runs php files on [http://mark.phillk.net/](http://mark.phillk.net/) but [http://www.greatwhitedata.com/index.php](http://www.greatwhitedata.com/index.php) it tries to send as a file.

What could be the issue?

---

### Post by stump138 on 2007-12-07
Is your http.conf set up properly for the 2nd site?  You can try posting it here to have a look.  

Going to [http://www.greatwhitedata.com](http://www.greatwhitedata.com) gives a 404 and the other tries to DL the file.  I'm initially thinking an apache issue because of that.

---

### Post by qwert231 on 2007-12-07
httpd.conf:
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

Include mod_mono.conf

I also tried reloading php5:
mark@linux800:/home/www/GreatWhite/logs$ sudo a2enmod php5 
This module is already enabled!
mark@linux800:/home/www/GreatWhite/logs$ sudo a2dismod php5
Module php5 disabled; run /etc/init.d/apache2 force-reload to fully disable.
mark@linux800:/home/www/GreatWhite/logs$ sudo /etc/init.d/apache2 reload
 * Reloading web server config...                                                                              5864
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Dec 07 14:53:39 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                                                        [ OK ]
mark@linux800:/home/www/GreatWhite/logs$ sudo a2enmod php5 
Module php5 installed; run /etc/init.d/apache2 force-reload to enable.
mark@linux800:/home/www/GreatWhite/logs$ sudo /etc/init.d/apache2 reload
 * Reloading web server config...                                                                              5864
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Dec 07 14:53:48 2007] [warn] NameVirtualHost *:0 has no VirtualHosts

---

