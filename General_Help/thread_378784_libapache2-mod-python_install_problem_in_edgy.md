---
title: "libapache2-mod-python install problem in edgy"
date: 2007-03-07
forum: General Help
---

### Post by Kemayo on 2007-03-07
I'm installing libapache2-mod-python with apt-get, and it doesn't seem to actually set up a working mod_python.

The apt-get install completes with no errors, but it doesn't create any mod_python files in /etc/apache2/mods-available, or in /usr/lib/apache2/modules.  /usr/lib/python2.4/site-packages/mod_python/ does exist, however.

Has anyone else run into this problem?

---

### Post by tronica on 2007-03-07
I believe you need to edit 

> /etc/httpd/conf.d/python.conf

and uncomment the line 

> LoadModule python_module modules/mod_python.so

then do a 

> /etc/init.d/apache2 restart

---

### Post by Kemayo on 2007-03-07
> **tronica said:**
> I believe you need to edit 

I don't have a /etc/httpd/conf.d/python.conf -- httpd is for apache1, apache2 uses /etc/apache2.  There's a conf.d folder in the apache2 folder, but it doesn't contain a python.conf.

---

### Post by tronica on 2007-03-07
make a back up of this file first

> cd /etc/apache2/sites-available/

Look for

> Options Indexes FollowSymLinks MultiViews
AllowOverride AuthConfig
Order allow,deny
allow from all
# Uncomment this directive is you want to see apache2's
# default start page (in /apache2-default) when you go to /
#RedirectMatch ^/$ /apache2-default/

change it to

>  Options Indexes FollowSymLinks MultiViews
AllowOverride AuthConfig
Order allow,deny
allow from all

AddHandler mod_python .py
PythonHandler mod_python.publisher
PythonDebug On

# Uncomment this directive is you want to see apache2's
# default start page (in /apache2-default) when you go to /
#RedirectMatch ^/$ /apache2-default/


i just did this on mine and it worked
the restart apache,

---

### Post by Kemayo on 2007-03-07
> **tronica said:**
> i just did this on mine and it worked
the restart apache,

This produces the result:
```
Invalid command 'PythonHandler', perhaps mis-spelled or defined by a module not included in the server configuration
```

---

### Post by tronica on 2007-03-07
give this a look, scroll down a bit:

[http://www.ubuntuforums.org/showthread.php?t=91101]("http://www.ubuntuforums.org/showthread.php?t=91101")

---

### Post by Kemayo on 2007-03-07
> **tronica said:**
> give this a look, scroll down a bit:

[http://www.ubuntuforums.org/showthread.php?t=91101]("http://www.ubuntuforums.org/showthread.php?t=91101")

Not applicable.  It assumes that the install worked:

```
sudo ln -s ../mods-available/mod_python.load mod_python.load
```

The mods-available/mod_python.load file doesn't exist.  (And anyway, using a2enmod would be an easier approach to accomplish that.)

---

