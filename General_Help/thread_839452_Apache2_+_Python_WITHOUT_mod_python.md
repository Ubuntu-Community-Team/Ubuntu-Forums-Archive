---
title: "Apache2 + Python WITHOUT mod_python"
date: 2008-06-24
forum: General Help
---

### Post by pistacchio on 2008-06-24
Hi to all!
How can i configure apache2 so that it processes all .py files with python without using mod_python?
I'm on Ubuntu 8.4.
Thanks in advance
Gustavo

---

### Post by pistacchio on 2008-06-25
anyone?

---

### Post by pistacchio on 2008-06-25
UPDATE:

currently my /etc/apache2/sites-available/default file reads:

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                #Options +ExecCGI Indexes FollowSymLinks MultiViews
                Options All
                AllowOverride None
                Order allow,deny
                Allow from all
                #AddHandler mod_python .py
                #PythonHandler mod_python.publisher
                #PythonDebug On

        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

```

---

### Post by pistacchio on 2008-06-25
Solved.
Here my new /etc/apache2/sites-available/default


```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        AddHandler cgi-script .py
        <Directory /var/www/>
                Options ExecCGI Indexes FollowSymLinks MultiViews
                #Options All
                AllowOverride None
                Order allow,deny
                allow from all
                #AddHandler mod_python .py
                #PythonHandler mod_python.publisher
                #PythonDebug On

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
```

---

### Post by elindstr on 2011-02-24
Thank you for taking the time to document your efforts.  Even though it was "all you", it ended up helping me out a lot.

Thanks again.

---

