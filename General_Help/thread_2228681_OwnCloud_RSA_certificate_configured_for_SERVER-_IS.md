---
title: "OwnCloud RSA certificate configured for SERVER- ISSUE, webpage has a redirect loop"
date: 2014-06-08
forum: General Help
---

### Post by alienprdkt on 2014-06-08
Let me first start by stating:
Yes, I have posted to owncloud forums as well :D

[COLOR=#000000][FONT=Arial]I had Owncloud running on a server that had died, I remember installing being easy, I have migrated server and Owncloud is one of the last apps to install.
Ok Just downloaded and installed the newest version of Owncloud on a Ubuntu 14.04 server with PHP 5.5.9-1, I am trying the manual install. I have tried adding repo and installing from apt-get install owncloud, did not work for me :/, whereis owncloud reported nothing. It's installed but never was able to bring up site.
Now for my issue I finished the manual install from .tar.bz2 when it came time to login I receive> [INDENT]"This webpage has a redirect loop"
[/INDENT]
, 
I receive the error from Chrome and Safari web browsers. I can't login at all, with no user, I get the error page.
Don't know if it is related or not but here's a look at the owncloud-error.log> [INDENT]"RSA certificate configured for "mysite.com" Does NOT include an ID which matches the server name"
[/INDENT]

Installed new ssl cert with CN as my ServerName directive in the vhost config file, same error :/ Re-installed owncloud same issue... Out of ideas.
So if anyone here can help with either issue:
a: "This webpage has a redirect loop" 
b: "RSA certificate configured for "mysite.com" Does NOT include an ID which matches the server name"

Please give me some options :)

Thanks in advance,
alienprdkt


[/FONT][/COLOR]

---

### Post by CharlesA on 2014-06-08
Sounds like a misconfigured web server to me.

Are you using the default LAMP stack or something else on 14.04?

Looks like you also posted your problem here:
[http://serverfault.com/questions/603740/owncloud-rsa-certificate-configured-for-server-issue-webpage-has-a-redirect-lo](http://serverfault.com/questions/603740/owncloud-rsa-certificate-configured-for-server-issue-webpage-has-a-redirect-lo)
and here:
[https://forum.owncloud.org/viewtopic.php?t=21723&p=61608](https://forum.owncloud.org/viewtopic.php?t=21723&p=61608)

We'd need more information to help you.

---

### Post by alienprdkt on 2014-06-08
Yes you are correct, posting all over loooking for help. This has been an all day joy ride, lol.
Sure what info would you need? 
Don't know how the webserver is misconfigured. I installed LAMP stack manually same procedure as my other 5 VM webservers.
 I also have webmin and 2 other sites hosted on the same server with no errors reported.

---

### Post by CharlesA on 2014-06-08
Can you post the virtualhost config you used for the owncloud server?

---

### Post by alienprdkt on 2014-06-08
Sure
> <VirtualHost *:52000>SSLEngine on
SSLCertificateFile /etc/apache2/ssl/owncloud.pem
SSLCertificateKeyFile /etc/apache2/ssl/owncloud.key

        ServerAdmin [EMAIL="webmaster@mysite.com"]webmaster@mysite.com[/EMAIL]

        ServerName mysite.com
        DocumentRoot /var/www/owncloud

        ErrorLog /var/log/apache2/cloud-error.log
        CustomLog /var/log/apache2/cloud-access.log combined


 </Directory>
<Directory /var/www/owncloud>
AllowOverride All
order allow,deny
Allow from all


 </Directory>


</VirtualHost>

also here is the default .htaccess file as well

> <IfModule mod_fcgid.c><IfModule mod_setenvif.c>
<IfModule mod_headers.c>
SetEnvIfNoCase ^Authorization$ "(.+)" XAUTHORIZATION=$1
RequestHeader set XAuthorization %{XAUTHORIZATION}e env=XAUTHORIZATION
</IfModule>
</IfModule>
</IfModule>
ErrorDocument 403 /core/templates/403.php
ErrorDocument 404 /core/templates/404.php
<IfModule mod_php5.c>
php_value upload_max_filesize 512M
php_value post_max_size 512M
php_value memory_limit 512M
php_value mbstring.func_overload 0
<IfModule env_module>
  SetEnv htaccessWorking true
</IfModule>
</IfModule>
<IfModule mod_rewrite.c>
RewriteEngine on
RewriteRule .* - [env=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
RewriteRule ^.well-known/host-meta /public.php?service=host-meta [QSA,L]
RewriteRule ^.well-known/carddav /remote.php/carddav/ [R]
RewriteRule ^.well-known/caldav /remote.php/caldav/ [R]
RewriteRule ^apps/([^/]*)/(.*\.(css|php))$ index.php?app=$1&getfile=$2 [QSA,L]
RewriteRule ^remote/(.*) remote.php [QSA,L]
</IfModule>
<IfModule mod_mime.c>
AddType image/svg+xml svg svgz
AddEncoding gzip svgz
</IfModule>
<IfModule mod_mime.c>
AddType image/svg+xml svg svgz
AddEncoding gzip svgz
</IfModule>
<IfModule dir_module>                                 
DirectoryIndex index.php index.html
</IfModule>
AddDefaultCharset utf-8
Options -Indexes
<IfModule pagespeed_module>
ModPagespeed Off
</IfModule>

---

### Post by CharlesA on 2014-06-08
How did you create owncloud.pem? Does apache give any errors when you restart it?

EDIT: Your config is all wrong.

See here:
[http://doc.owncloud.org/server/6.0/admin_manual/installation/installation_source.html](http://doc.owncloud.org/server/6.0/admin_manual/installation/installation_source.html)

---

### Post by alienprdkt on 2014-06-08
Followed this guide: [http://sharadchhetri.com/2013/05/24/how-to-configure-self-signed-ssl-certificate-in-owncloud-ubuntu/](http://sharadchhetri.com/2013/05/24/how-to-configure-self-signed-ssl-certificate-in-owncloud-ubuntu/)

No errors reported upon startup in terminal, but the error is there in the cloud-error.log upon starting Apache.

---

### Post by CharlesA on 2014-06-08
> **alienprdkt said:**
> Followed this guide: [http://sharadchhetri.com/2013/05/24/how-to-configure-self-signed-ssl-certificate-in-owncloud-ubuntu/](http://sharadchhetri.com/2013/05/24/how-to-configure-self-signed-ssl-certificate-in-owncloud-ubuntu/)

No errors reported upon startup in terminal, but the error is there in the cloud-error.log upon starting Apache.

That looks fine for creating a self signed ssl cert (with browsers will complain about), but it shouldn't have any other effect.

You also have an extra </Directory> directive.

Try using the apache config from the owncloud site.

```
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
        ServerName YourServerName
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined
        SSLEngine on
        SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>
        BrowserMatch "MSIE [2-6]" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
        <Directory /var/www/owncloud>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                Allow from all
                # add any possibly required additional directives here
                # e.g. the Satisfy directive (see below for details):
                Satisfy Any
        </Directory>
</VirtualHost>
</IfModule>
```

---

### Post by alienprdkt on 2014-06-08
Think I was one step ahead of you, I edited the default-ssl.conf file to fit owncloud. Here is my updated file:

> <IfModule mod_ssl.c>        <VirtualHost _default_:52000>
                ServerAdmin webmaster@localhost


                DocumentRoot /var/www/owncloud


                # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
                # error, crit, alert, emerg.
                # It is also possible to configure the loglevel for particular
                # modules, e.g.
                #LogLevel info ssl:warn


                ErrorLog ${APACHE_LOG_DIR}/owncloud.error.log
                CustomLog ${APACHE_LOG_DIR}/owncloud.access.log combined


                #   SSL Engine Switch:
                #   Enable/Disable SSL for this virtual host.
                SSLEngine on


                #   A self-signed (snakeoil) certificate can be created by installing
                #   the ssl-cert package. See
                #   /usr/share/doc/apache2/README.Debian.gz for more info.
                #   If both key and certificate are stored in the same file, only the
                #   SSLCertificateFile directive is needed.
                SSLCertificateFile      /etc/apache2/ssl/owncloud.pem
                SSLCertificateKeyFile /etc/apache2/ssl/owncloud.key


                #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                                SSLOptions +StdEnvVars
                </FilesMatch>
                <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
                </Directory>


                BrowserMatch "MSIE [2-6]" \
                                nokeepalive ssl-unclean-shutdown \
                                downgrade-1.0 force-response-1.0
                # MSIE 7 and newer should be able to use keepalive
                BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown


# Have apache 2.4
<Directory /var/www/owncloud>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All
    Require all granted
</Directory>


        </VirtualHost>
</IfModule>




Fixed my error in cloud-error.log :D

Ok cleared cookies, brought up owncloud login page, enter credentials click login get the error
 > [CENTER][COLOR=#666666][FONT=Helvetica]This webpage has a redirect loop[/FONT][/COLOR][/CENTER]
  :(

One error fixed :) now if I could log in.

---

### Post by CharlesA on 2014-06-08
Do you have mod rewrite enabled in apache?

---

### Post by alienprdkt on 2014-06-08
a2enmod rewrite
Module rewrite already enabled

---

### Post by CharlesA on 2014-06-08
Clear your browser cache and see what happens.

---

### Post by alienprdkt on 2014-06-08
Tried, cleared browser cache as well as cookies, same issue: Both Chrome & Safari browsers

---

### Post by CharlesA on 2014-06-08
Check your error and access logs. Still sounds like something is not set up right.

---

### Post by alienprdkt on 2014-06-08
Checked logs nothing, we cleared the only error that was being logged. No errors reported in access.log

---

### Post by CharlesA on 2014-06-08
Remove the symlink for the default ssl site in /etc/apache2/sites-enabled/default-ssl and add a completely new virtual host with just this in it.

```
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
        ServerName YourServerName
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/owncloud
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined
        SSLEngine on
        SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>
        BrowserMatch "MSIE [2-6]" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
        <Directory /var/www/owncloud>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                Allow from all
                # add any possibly required additional directives here
                # e.g. the Satisfy directive (see below for details):
                Satisfy Any
        </Directory>
</VirtualHost>
</IfModule>
```

Leave it at port 443 to test and see it you can login or not.

---

### Post by alienprdkt on 2014-06-09
still same issue :/

---

### Post by CharlesA on 2014-06-09
Get rid of your default site and see if the same problem occurs.

I just tested it on a VM and it worked as expected.

---

### Post by alienprdkt on 2014-06-09
Grrrrrrr' wish I knew what was up, dont have time to reset up a new server... 

same issues... heres my permissions:

are yours the same?

> drwxr-xr-x 22 www-data www-data  4096 Jun  8 19:22 3rdpartydrwxr-xr-x 26 www-data www-data  4096 Jun  8 19:22 apps
-rw-r--r--  1 www-data www-data   586 Jun  8 19:22 AUTHORS
drwxr-xr-x  2 www-data www-data  4096 Jun  8 19:23 config
-rw-r--r--  1 www-data www-data   916 Jun  8 19:22 console.php
-rw-r--r--  1 www-data www-data 34520 Jun  8 19:22 COPYING-AGPL
drwxr-xr-x 14 www-data www-data  4096 Jun  8 19:22 core
-rw-r--r--  1 www-data www-data  3480 Jun  8 19:22 cron.php
drwxrwx---  3 www-data www-data  4096 Jun  8 19:25 data
-rw-r--r--  1 www-data www-data 24040 Jun  8 19:22 db_structure.xml
-rw-r--r--  1 www-data www-data  1230 Jun  9 00:12 .htaccess
-rw-r--r--  1 www-data www-data   179 Jun  8 19:22 index.html
-rw-r--r--  1 www-data www-data  1084 Jun  8 19:22 index.php
drwxr-xr-x 99 www-data www-data  4096 Jun  8 19:22 l10n
drwxr-xr-x  5 www-data www-data  4096 Jun  8 19:22 lib
-rw-r--r--  1 www-data www-data   279 Jun  8 19:22 occ
drwxr-xr-x  2 www-data www-data  4096 Jun  8 19:22 ocs
-rw-r--r--  1 www-data www-data   806 Jun  8 19:22 public.php
-rw-r--r--  1 www-data www-data  1212 Jun  8 19:22 remote.php
-rw-r--r--  1 www-data www-data    26 Jun  8 19:22 robots.txt
drwxr-xr-x  6 www-data www-data  4096 Jun  8 19:22 search
drwxr-xr-x  9 www-data www-data  4096 Jun  8 19:22 settings
-rw-r--r--  1 www-data www-data  1447 Jun  8 19:22 status.php
drwxr-xr-x  2 www-data www-data  4096 Jun  8 19:22 themes
-rw-r--r--  1 www-data www-data   149 Jun  8 19:22 version.php

And you used that same file vhost config file you showed me?
This is really odd... I will test an install in a VM as well and see if I can have better outcome?
Thanks for your help.

---

### Post by CharlesA on 2014-06-09
Looks right. All I did after I extracted the tar was to change the owner and group to www-data.

It sounds like you have a redirect somewhere in your config, but if you are accessing the page via https, that shouldn't be it.

Note, I had to enabled ssl and rewrite, but I think you already have both those installed and enabled.

---

### Post by alienprdkt on 2014-06-09
Thanks again, I'd hate to start over on this server :/
Will try to put in kVM and NFS Export owncloud user drives from other server.

---

### Post by CharlesA on 2014-06-09
I have a feeling trying to add it via the repo mucked things up. I've always done it manually cuz I use Nginx, but it isn't that difficult overall.

Have you checked for other config files?

---

### Post by alienprdkt on 2014-06-09
Thats my guess too, I have installed this before without issues, was actually surprised how easy setup was, of course installed manually first time. It was weird I installed it from repo but it didnt create a vhost.conf file, nor was able to find it with the command: > whereis owncloud, that probably was the issue. But will just have a kVM and run my user profiles via NFS. Seems to be the easiest work-around for me at the moment. 

Thanks again for your help for me to determine that it is not owncloud and is in fact my server :/

---

### Post by CharlesA on 2014-06-09
Did you purge owncloud after the repo version didn't work?

```
sudo apt-get purge owncloud
```

That might get it working, but I don't know for sure.

---

