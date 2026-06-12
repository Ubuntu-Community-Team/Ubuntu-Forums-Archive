---
title: "Apache2 help - SSL installed but site stopped working.  Redirect issue"
date: 2018-05-16
forum: General Help
---

### Post by U2XS on 2018-05-16
Following this tutorial ([https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-14-04)) I added SSL to my site.  However when I did, it stopped working.  

If I disable http redirect I can still access the non-ssl site.  However when I go to https I get a "this page is not working" "ERR_TOO_MANY_REDIRECTS" message.  The too many redirect message is telling.  Also the access log has about 8 rows for every visit.  So I can tell that there is a loop somewhere.  Howevever the error log shows nothing.

My http conf file looks like this

```
<VirtualHost *:80>
    ServerName tutorial.hlx.co
    ServerAlias tutorial.hlx.co 172.104.11.52
    WSGIScriptAlias / /home/admin/odoo/odoo_wsgi.py
    WSGIDaemonProcess odooerp1 user=admin group=admin processes=2 python-path=/home/admin/odoo display-name=apache-odoo
    WSGIProcessGroup odooerp1
    ErrorLog /home/admin/error-odoo.log
    CustomLog /home/admin/access-odoo.log combined
    <Directory /home/admin/odoo>
        AllowOverride None
        Require all granted
    </Directory>
RewriteEngine on
RewriteCond %{SERVER_NAME} =172.104.11.52 [OR]
RewriteCond %{SERVER_NAME} =tutorial.hlx.co
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>

```

My https conf file looks like this


```
<IfModule mod_ssl.c>
<VirtualHost *:443>
    ServerName tutorial.hlx.co
    ServerAlias tutorial.hlx.co 172.104.11.52
    WSGIScriptAlias / /home/admin/odoo/odoo_wsgi.py
    WSGIDaemonProcess odooerp user=admin group=admin processes=2 python-path=/home/admin/odoo display-name=apache-odoo
    WSGIProcessGroup odooerp
    ErrorLog /home/admin/error-odoo.log
    CustomLog /home/admin/access-odoo.log combined
    <Directory /home/admin/odoo>
        AllowOverride None
        Require all granted
    </Directory>
SSLCertificateFile /etc/letsencrypt/live/tutorial.hlx.co/fullchain.pem
SSLCertificateKeyFile /etc/letsencrypt/live/tutorial.hlx.co/privkey.pem
Include /etc/letsencrypt/options-ssl-apache.conf
</VirtualHost>
</IfModule>
```

---

### Post by SeijiSensei on 2018-05-16
Try this for your HTTP configuration:

```

<VirtualHost *:80>
ServerName tutorial.hlx.co

Redirect / https://tutorial.hlx.co/
</VirtualHost>

```
This redirects all HTTP requests to the HTTPS port. That works reliably for me.

Did you run "sudo a2enmod ssl" and restart the apache2 server? If you're really running 14.04, then you'd need to use "sudo service apache2 restart".  More recent distributions require "sudo systemctl restart apache2".

---

