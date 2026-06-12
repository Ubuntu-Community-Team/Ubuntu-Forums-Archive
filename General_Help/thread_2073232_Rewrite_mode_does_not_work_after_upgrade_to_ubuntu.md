---
title: "Rewrite mode does not work after upgrade to ubuntu 12.10"
date: 2012-10-19
forum: General Help
---

### Post by lubart on 2012-10-19
Hi!

I have a problem with rewrite mode on my local web-server (apache2) after ubuntu upgrade and now I have not access to my projects. Localhost and virtual host works fine, I can go to [http://localhost](http://localhost) myproject and to [http://myhost.home](http://myhost.home). But for zend-framework projects I need rewrite_mod and I have not access to address [http://myhost.home/index/](http://myhost.home/index/).

After

sudo a2enmod rewrite

I have "Module rewrite already enabled"

also in my /etc/apache2/sites-available/myhost.home I have:

<VirtualHost *:80>
ServerName myhost.home
DocumentRoot /home/slava/server/myhost/public/
SetEnv APPLICATION_ENV development
<Directory /home/slava/server/myhost/public/>
    Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
</Directory>

</VirtualHost>

in my /home/slava/server/myhost/public/.htaccess I have

RewriteEngine On
RewriteCond %{REQUEST_FILENAME} -s [OR]
RewriteCond %{REQUEST_FILENAME} -l [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^.*$ - [NC,L]
RewriteRule ^.*$ index.php [NC,L]

Everything looks good (for me :)) but it does not work! .htaccess file I did not change and system worked with it before upgrade. Can someone help me?

Thank you!

---

### Post by CrowderSoup on 2012-10-20
I too am experiencing a similar issue. I have noticed that it will rewrite "hostname.com/Index" but not "hostname.com/index".

This is a very strange issue and didn't manifest itself until after the upgrade to 12.10. Is this a bug with this particular build of Apache?

---

### Post by kamilsj on 2012-10-20
Exactly the same issue ... I tried everything and I could not find a solution. There has to be an error in apache2!

Cheers

---

### Post by zven on 2012-10-22
same here. cannot access my webprojects - i found this but cannot fix this myself...
[http://askubuntu.com/questions/192680/i-upgraded-my-server-to-12-10-why-does-php-not-work-with-nginx](http://askubuntu.com/questions/192680/i-upgraded-my-server-to-12-10-why-does-php-not-work-with-nginx)

---

### Post by zven on 2012-10-22
i got it working again by editing:
/etc/apache2/mods-available/php5.conf
and uncommenting the line 
```
php_admin_value engine Off
```
to
```
# php_admin_value engine Off
```

---

### Post by CrowderSoup on 2012-10-23
I got it working also! However, I did so by turning off MultiViews in my V-Host.

---

### Post by ~LoKe on 2012-10-23
Some have resorted to downgrading PHP.

---

### Post by grzemach on 2013-01-31
[http://stackoverflow.com/questions/13548174/htaccess-refuses-to-redirect-urls-without-file-extensions-straight-to-404](http://stackoverflow.com/questions/13548174/htaccess-refuses-to-redirect-urls-without-file-extensions-straight-to-404)
this has help me.

```
a2dismod negotiation
``` & restart apache & working.

---

