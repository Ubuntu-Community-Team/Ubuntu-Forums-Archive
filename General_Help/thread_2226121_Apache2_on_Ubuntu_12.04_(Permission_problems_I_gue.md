---
title: "Apache2 on Ubuntu 12.04 (Permission problems I guess)"
date: 2014-05-25
forum: General Help
---

### Post by disabled20191128 on 2014-05-25
So i decided to create an apache2 server, and move its root directory.

sudo apt-get install apache2

Then in order to make my changes I turned it off with:

sudo service apache2 stop

Then I made the directory modification:

sudo gedit /etc/apache2/sites-available/default

"DocumentRoot /var/www" to "DocumentRoot /home/dennis/Apache2"
"<Directory /var/www/>" to "<Directory /home/dennis/Apache2/>"

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/dennis/Apache2
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/dennis/Apache2/>
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
"

I then made sure default was enabled 

sudo a2ensite default

And finally restarted the server

sudo service apache2 start

But when I went to localhost i got this message:

[h=1]Forbidden[/h] You don't have permission to access / on this server.
 [HR][/HR] Apache/2.2.22 (Ubuntu) Server at localhost Port 80


Could anybody tell me what is wrong?

---

### Post by SeijiSensei on 2014-05-25
You should have 755 permissions on /home/dennis/Apache2 and 644 permissions on the files it contains.  Apache runs as user "www-data" so you need to grant 
"others" read and execute privileges on all the site's directories and read privileges on all files.
```

cd /home/dennis
chmod 755 Apache2
chmod 644 Apache2/*.html

```

Usually those are the defaults Ubuntu uses for new directories and files.  Type the command "umask" at the prompt.  Do you get something other than the default value "0002"?

---

### Post by disabled20191128 on 2014-05-25
Even after setting the permissions i am still getting the same message:
[h=1]Forbidden[/h] You don't have permission to access / on this server.
 [HR][/HR] Apache/2.2.22 (Ubuntu) Server at localhost Port 80

And umask only returns 0002

Do you have any other ideas?

---

### Post by disabled20191128 on 2014-05-25
Could the fact that my home directory is encrypted interfere with Apache2?

---

### Post by SeijiSensei on 2014-05-26
Try this:
```

$ sudo su
# su www-data
$ ls /home/dennis/Apache2
$ exit
# exit

```
Can you list the directory after becoming the www-data user?

I've never used encrypted home directories; maybe that's the problem.

---

