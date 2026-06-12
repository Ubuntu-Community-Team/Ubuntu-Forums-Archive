---
title: "how to change document root apache"
date: 2007-02-22
forum: General Help
---

### Post by jeisma on 2007-02-22
hi!

i'm trying to change the document root of apache in xubuntu6.10.

from a working apache install in rhel, i copied the following:

DocumentRoot "/var/www/html"
<Directory "/var/www/html">

inserted in /etc/apache2/apache2.conf in the xubuntu box. changed it to /data/www.

i get <Directory> was not closed when im trying to restart apache.

thinking it might be permission problem, i chmod 777 www. 

what could be missing in my config. i created /data during install of xubuntu.

help pls?

thanks!

joey

---

### Post by llamakc on 2007-02-22
The DocumentRoot declaration doesn't go in /etc/apache2/apache2.conf. Instead, make that change in /etc/apache2/sites-available/default

After you have done this, run:

sudo apache2ctl -t

And then

sud apache2ctl restart

HTH

---

