---
title: "redirect wildcard host name to respective directory"
date: 2015-07-21
forum: General Help
---

### Post by ELMIT on 2015-07-21
I have setup DNS to my new site with wildcard

Then I tried to ping any name and it responded. Seems DNS is ok.

Next I setup Apache config file:

> <VirtualHost *:80>
    ServerName xxx.net
    ServerAlias *.xxx.net
    ServerAdmin [email]ronald+xxx.net@xxx.com[/email]
    DocumentRoot /var/www/xxx.net
    <Directory /var/www/elmit.net>
       Options Indexes FollowSymLinks MultiViews
       AllowOverride All
       Order allow,deny
       allow from all
    </Directory>
   ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

I created the directories /var/www/xxx.net/shops/admin and /var/www.xxx.net/shops/firstshop

I created in /var/www/xxx.net a .htaccess file:

> RewriteEngine on
RewriteBase /
RewriteCond %{HTTP_HOST} ^(www\.)?[^.]+\.xxx\.net.*$
RewriteRule (.*) shops/$1 [L]

I enabled the new site and reloaded apache. I even restarted apache.

Whatever host I try I get a maintenance screen. Not even knowing from where this one might come. Other hosts/domains are still working fine.

What am I missing?

---

