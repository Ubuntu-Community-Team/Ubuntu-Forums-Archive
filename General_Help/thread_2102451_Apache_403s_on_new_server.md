---
title: "Apache 403s on new server"
date: 2013-01-07
forum: General Help
---

### Post by ellepea on 2013-01-07
Hello all,

I am a new convert to Ubuntu, and moving some VERY OLD redhat servers to new Ubuntu servers. I am having some problems with the apache installs though. I seem to have figured everything out except that I am getting 403s on symbolic links. 

We have two hostnames currently pointed to the server, one being the main hostname of the server. 

our.server.com (/var/www/html/a/docs)
website.com (/var/www/html/website/docs)

website.com has a symbolic link that points default.html to website.html which are both in the same directory.

```
-rwxr-xr-x 1 ftpuser lusers   4389 Jan  5 13:58 website.html
lrwxrwxrwx 1 ftpuser lusers   13 Jan  5 13:57 default.html -> website.html
```

I am getting a 403 when I try to access default.html. Accessing website.html is not a problem.

Here are the config files:

/etc/apache2/sites-enabled/000-default

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/html/a/docs
        <Directory />
                Options +Includes +FollowSymLinks +ExecCGI
                AllowOverride None
        </Directory>
        <Directory /var/www/html/a/docs>
                Options +Indexes +Includes +FollowSymLinks +ExecCGI
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
        <Directory /var/www/html>
                Options +Indexes +Includes +FollowSymLinks +ExecCGI +MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride All
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

/etc/apache2/sites-enabled/website.com

```
<VirtualHost *:80>
   ServerAdmin sysadmin@actioncorporation.com
   DocumentRoot /var/www/html/website/docs
   ServerName website.com
   ServerAlias www.website.com
   ErrorLog /var/www/html/website/logs/error
   CustomLog /var/www/html/website/logs/access combined
   Options Includes
</VirtualHost>
```

Thank you for any help!!!

---

### Post by slickymaster on 2013-01-07
It could be due to permissions on the filesystem. Does the file in the directory that you are symlinking have read/execute permissions?

---

