---
title: "Apache 2 Subdomains -- Trouble with Alphabetical Order"
date: 2013-08-12
forum: General Help
---

### Post by dakong27 on 2013-08-12
I have a main site, say, [www.greatnews.com]("http://www.greatnews.com").  Its vhost file in sites-available is

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName www.greatnews.com

        DocumentRoot /var/www
        <Directory /var/www/modx/>
                Options Indexes FollowSymLinks +ExecCGI MultiViews 
                AllowOverride all 
                Order allow,deny
                allow from all 
                AddHandler cgi-script .cgi .pl 
        </Directory>
        ScriptAlias /cgi-bin/ /var/www/cgi-bin/
        <Directory "/var/www/cgi-bin">
                AllowOverride all 
                Options Indexes FollowSymLinks +ExecCGI MultiViews 
                Order allow,deny
                Allow from all 
                AddHandler default-handler .css .html .pdf .jpg .gif .png
        </Directory>
</VirtualHost>

```

I am trying to set up a subdomain, map.greatnews.com, with this vhost file:

```
NameVirtualHost *:80

<VirtualHost *:80>
   ServerName map.greatnews.com
   ServerAlias map.greatnews.com
   DocumentRoot /var/www/map/app
   DirectoryIndex index.php
   <Directory /var/www/map/app/>
      AllowOverride All 
      Order Allow,Deny
      Allow from all 
   </Directory>
</VirtualHost>

```

I have the

```
NameVirtualHost *:80 
```

in the ports.conf file and an * A record with my registrar to direct all subdomains to my same static IP address.  I have issued ```
a2ensite
``` and ```
service apache2 reload
``` and both the main vhost file and the subdomain vhost file show up in sites-enabled, so I know they took.

I cannot for the life of me get the subdomain map.greatnews.com site to appear, always only getting [www.greatnews.com]("http://www.greatnews.com") unless I change the name of the subdomain to ap.greatnews.com such that it appears higher in the alphabetical order than [www.greatnews.com]("http://www.greatnews.com") in the sites-available vhost file names.  I am sure the problem is Apache2 is grabbing the first thing in the sites-enabled list of files, [www.greatnews.com]("http://www.greatnews.com"), seeing that the DocumentRoot says /var/www, and calling it a day without bothering to check anything else further down the alphabetical order that would better fit the URL requested.  But I cannot force any different behavior, despite having avoided over-greedy wildcards in the ServerAlias in [www.greatnews.com]("http://www.greatnews.com") to force it to find a better match later.

Does anyone know of a better solution to the pesky alphabetical problem?

---

### Post by SeijiSensei on 2013-08-12
From here [www.greatnews.com](www.greatnews.com) brings up a placeholder page, but map.greatnews.com returns a "host unknown." A DNS lookup for that name also reports that it does not exist. Create a DNS entry for map.greatnews.com with a CNAME that points to [www.greatnews.com](www.greatnews.com) and see if that helps.

---

