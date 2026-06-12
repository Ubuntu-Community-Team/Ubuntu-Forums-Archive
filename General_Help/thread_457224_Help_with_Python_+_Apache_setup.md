---
title: "Help with Python + Apache setup"
date: 2007-05-28
forum: General Help
---

### Post by daelus on 2007-05-28
I'm having problems getting python to work correctly with apache.  I created a simply hello world app in a file called test.py in my Python directory.  Whenever I hit the file, it causes a file open/save prompt to open in my web browser.  I also tried the install method on ubuntuguide, but I get the same results.

I've followed the setup instructions listed here:
[http://robrohan.com/2006/10/01/howto-setup-python-for-web-development-on-ubuntu/](http://robrohan.com/2006/10/01/howto-setup-python-for-web-development-on-ubuntu/)

Here's the tail from error log after restarting apache and hitting the python file:
```
[Mon May 28 12:27:12 2007] [error] python_init: Python version mismatch, expected '2.5', found '2.5.1'.
[Mon May 28 12:27:12 2007] [error] python_init: Python executable found '/usr/bin/python'.
[Mon May 28 12:27:12 2007] [error] python_init: Python path being used '/usr/lib/python25.zip:/usr/lib/python2.5/:/usr/lib/python2.5/plat-linux2:/usr/lib/python2.5/lib-tk:/usr/lib/python2.5/lib-dynload'.
[Mon May 28 12:27:12 2007] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Mon May 28 12:27:12 2007] [notice] mod_python: using mutex_directory /tmp 
[Mon May 28 12:27:13 2007] [notice] Apache/2.2.3 (Ubuntu) DAV/2 SVN/1.4.3 mod_python/3.2.10 Python/2.5.1 PHP/5.2.1 configured -- resuming normal operations
[Mon May 28 12:27:43 2007] [notice] mod_python: (Re)importing module 'mod_python.publisher'
[Mon May 28 12:27:44 2007] [notice] [client 192.168.1.1] Publisher loading page /var/www/Python/test.py
[Mon May 28 14:15:53 2007] [notice] mod_python: (Re)importing module 'mod_python.publisher'
[Mon May 28 14:15:53 2007] [notice] [client 192.168.1.1] Publisher loading page /var/www/Python/test.py

```

I have symbolic links going from my ~/www/Python directory to my /var/www/ root directory, and here's my apache config file:
```
NameVirtualHost *
<VirtualHost *>

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www

        ErrorLog /var/log/apache2/error.log
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

        # Default settings for all sites
        <Directory />
                Options FollowSymLinks -ExecCGI
                AllowOverride none
                Order allow,deny
                Allow from all
                # Python Stuff
                AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On
        </Directory>

        # "Main" website
        <Directory /var/www/>
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                Allow from all
                # Redirect to this dir when the base url is hit
                RedirectMatch ^/$ /Personal/
        </Directory>

        # Python directory - should be covered by default, but who knows
        <Directory /var/www/Python>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                Allow from all
                # Python stuff
                AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On
        </Directory>

        # cgi-bin directory
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        # Apache2 doc folder
        Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
                Options MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

        # WebSVN: uses subversion's passwd file for auth
        # (same passwd file used when http://localhost/svn is it)
        <Directory /var/www/websvn/>
                AllowOverride None
                AuthUserFile /etc/apache2/dav_svn.passwd
                AuthName "Subversion Repository Access"
                AuthType Basic
                Require valid-user
                <IfModule mod_php5.c>
                        php_flag magic_quotes_gpc Off
                        php_flag track_vars On
                </IfModule>
        </Directory>

     
</VirtualHost>

```

Thanks for any help in advance.

---

### Post by daelus on 2007-05-28
Blah.  After struggling with this for three hours today, I found the problem.  It was with the python script itself. Unlike php, there doesn't seem to be a default content type set.

Here's the code that finally got the script to work for me:
```
def index(req):
	req.content_type = "text/plain"
	req.write("Hellow World")

```

---

