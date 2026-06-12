---
title: "Apache and 403 forbidden error"
date: 2023-06-08
forum: General Help
---

### Post by lx431 on 2023-06-08
Hi there, I speak about a new install of AMP on Ubuntu 23.04
I would change the default root from /var/www/html to /home/myuser/website

I've edited (with nano):

 /etc/apache2/apache2.conf 
[HTML]<Directory /home/myuser/website>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>
[/HTML]

and /etc/apache2/sites-available/000-default.conf
[HTML]DocumentRoot /home/myuser/website[/HTML]
nothing else.

Rebooting Apache 2.4 but on [http://localhost](http://localhost) I get: 403 forbidden

Where I wrong?

---

### Post by TheFu on 2023-06-10
You need to check all the permissions for every parent directory and ensure the userid running apache has access, at a minimum.

However, placing a website that isn't using Apache's mod_public model in a HOME directory is a huge mistake. Best not to do that and to place the websites in /var/www/ instead.  If you want to make accessing it easier, create a symbolic link from your HOME to that other location.

BTW, wouldn't hurt to run apache's config file checker too.

---

