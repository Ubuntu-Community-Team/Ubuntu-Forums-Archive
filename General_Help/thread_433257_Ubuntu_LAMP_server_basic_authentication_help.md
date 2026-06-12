---
title: "Ubuntu LAMP server basic authentication help"
date: 2007-05-04
forum: General Help
---

### Post by muzgash15 on 2007-05-04
Hey everyone I'm running an Ubuntu LAMP server 6.06.  I'm new to apache2.0.55 and I've been attempting to configure it so I can download files from my Samba shares wherever I am.  I have everything setup how I want it but I can't get basic authentication to work, I've read every piece of documentation/tutorial I could find and I'm a bit stuck.  Here's my setup.

/var/www/share is a simlink to /home/shares/allusers (the samba share i want password protected) I can access it over the web just fine.  However, when I try to setup basic authentication the directory disappears from the index on the webpage.  I've tried both the edit apache2.conf method and the .htaccess method.

First, I used this command to create my password file:
/usr/bin/htpasswd -c /etc/apache2/.htpasswd user

Second, I edited /etc/apache2/sites-available/default to look like this:
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
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



Third, I tried the edit apache2.conf method, I appended this to /etc/apache2/apache2.conf:
# AUTHENTICATION
<Directory /var/www/share/window/>
AllowOverride All
AuthName "Secure Server Access"
AuthType Basic
AuthUserFile /etc/apache2/.htpasswd
Require valid-user
</Directory>

This made the directory disappear so I attempted to do this with .htaccess.

I changed the edit I made to apache2.conf to this:
# AUTHENTICATION
<Directory /var/www/share/window/>
AllowOverride All
#AuthName "Secure Server Access"
#AuthType Basic
#AuthUserFile /etc/apache2/.htpasswd
#Require valid-user
</Directory>

Then, I put this in /var/www/share/window/.htaccess:
#<Directory /var/www/share/window/>
AuthName "Secure Server Access"
AuthType Basic
AuthUserFile /etc/apache2/.htpasswd
Require valid-user
#</Directory>

This also made that directory completely disappear from my index.  Anyone have any ideas?  Oh and what's the syntax I use to format the code properly?  I attempted <code> </code> but it didn't work.

---

### Post by muzgash15 on 2007-05-04
Sorry about the re-post but I figured out the syntax to tag my examples.  I hope this makes it easier to read.

First, I used this command to create my password file:
```

/usr/bin/htpasswd -c /etc/apache2/.htpasswd user

```

Second, I edited /etc/apache2/sites-available/default to look like this:
```

NameVirtualHost *
<VirtualHost *>
ServerAdmin webmaster@localhost

DocumentRoot /var/www
<Directory />
Options FollowSymLinks
AllowOverride All
</Directory>
<Directory /var/www/>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
allow from all
# Uncomment this directive is you want to see apache2's
# default start page (in /apache2-default) when you go to /
#RedirectMatch ^/$ /apache2-default/
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


Third, I tried the edit apache2.conf method, I appended this to /etc/apache2/apache2.conf:
```

# AUTHENTICATION
<Directory /var/www/share/window/>
AllowOverride All
AuthName "Secure Server Access"
AuthType Basic
AuthUserFile /etc/apache2/.htpasswd
Require valid-user
</Directory>

```

This made the directory disappear so I attempted to do this with .htaccess.

I changed the edit I made to apache2.conf to this:
```

# AUTHENTICATION
<Directory /var/www/share/window/>
AllowOverride All
#AuthName "Secure Server Access"
#AuthType Basic
#AuthUserFile /etc/apache2/.htpasswd
#Require valid-user
</Directory>

```
Then, I put this in /var/www/share/window/.htaccess:
```

#<Directory /var/www/share/window/>
AuthName "Secure Server Access"
AuthType Basic
AuthUserFile /etc/apache2/.htpasswd
Require valid-user
#</Directory>

```

---

