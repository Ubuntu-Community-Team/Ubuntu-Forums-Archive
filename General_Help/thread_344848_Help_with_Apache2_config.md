---
title: "Help with Apache2 config"
date: 2007-01-23
forum: General Help
---

### Post by Spano on 2007-01-23
I am trying to set up a server with Apache2 and virtual hosting.
I can see my test page on the LAN at [http://10.0.0.17/index.html](http://10.0.0.17/index.html)

No one outside the LAN can see my test page, but they can see Apache default page or Apache error pages depending on my settings.

my address is [http://project1.zapto.org](http://project1.zapto.org)
My test page is at /var/www/project1/index.html

here is my /etc/apache2/sites-available/project1
it is symlinked to /etc/apache2/sites-enabled/project1 

NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName project1.zapto.org
        DocumentRoot /var/www/project1/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/project1>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

Aside from this file, I have not made any configuration changes to Apache.
I'm using no-ip to update my dynamic IP and have port 80 forwarded through my DSL modem.  Port 80 is not being blocked by my ISP.

Thanks much for any help.  This is  driving me nuts.

---

### Post by Spano on 2007-01-23
And there's more!
I have changed  owner and permissions of /var/www with:

```
#chown -R daniel /var/www
#chmod -R 755 /var/www
```

---

### Post by Spano on 2007-01-28
This solved my problem - comment out the redirect.  Make this
```
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
RedirectMatch ^/$ /apache2-default/
</Directory>
```
Look like this
```
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
#RedirectMatch ^/$ /apache2-default/
</Directory>
```

---

