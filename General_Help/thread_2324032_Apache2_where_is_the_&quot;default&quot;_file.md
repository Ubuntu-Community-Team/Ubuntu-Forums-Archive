---
title: "Apache2 where is the &quot;default&quot; file"
date: 2016-05-10
forum: General Help
---

### Post by satimis on 2016-05-10
Hi all,

Ubuntu 16.04

I'm following;
midPoint on Ubuntu, Tomcat, PostgreSQL HOWTO
[https://wiki.evolveum.com/display/midPoint/midPoint+on+Ubuntu,+Tomcat,+PostgreSQL+HOWTO](https://wiki.evolveum.com/display/midPoint/midPoint+on+Ubuntu,+Tomcat,+PostgreSQL+HOWTO)

to install midPoint

Coming to;
Configure the proxy to tomcat in appropriate apache site definition:

I couldn't find /etc/apache2/sites-available/default file.

&#10219; ls /etc/apache2/sites-available/```

000-default.conf  default-ssl.conf

```

Please advise where can I find the "default" file?

Thanks

Regards
satimis

---

### Post by mcduck on 2016-05-10
It's either one of the two files you are looking at right now, depending on if you want SSL or not.

There used to be one "default" file, but current Apache version gives you two different options instead. Just use the one you want as template for making your own configuration. I guess your instructions are for older Ubuntu version that what you are running. I recommend using the official server guide: [https://help.ubuntu.com/lts/serverguide/]("https://help.ubuntu.com/lts/serverguide/")

---

### Post by Habitual on 2016-05-10
/etc/apache2/sites-enabled/000-default is the default "site".
```
a2ensite 000-default
``` will tell you it's status.

/etc/apache2/sites-enabled/000-default is a symlink to /etc/apache2/sites-available/default
so, if you can't "find" /etc/apache2/sites-available/default then 000-default would not start, nor serve.

/etc/apache2/sites-available/default 
```
<VirtualHost *:80>
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

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
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
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

It's my opinion that if this is the sole site on the server, make your 
midPoint edits in the file at /etc/apache2/sites-enabled/000-default

Good Luck.

---

