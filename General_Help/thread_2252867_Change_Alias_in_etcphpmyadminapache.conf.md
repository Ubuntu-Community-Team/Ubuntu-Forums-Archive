---
title: "Change Alias in /etc/phpmyadmin/apache.conf"
date: 2014-11-15
forum: General Help
---

### Post by charitosha on 2014-11-15
Hello.
Although this subject has been beaten to death, i managed to have some problems too...
At phpMyAdmin i get the following error:
#1045 Cannot log in to the MySQL server

Now as i was trying to solve it, i noticed that during the start/stop or restart command of apache i get the following:
The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

here's what is in line 3:
Alias /phpmyadmin /usr/share/phpmyadmin

How do i change it so i won't have this problem with the Alias???

---

### Post by dragonfly41 on 2014-11-15
I'm currently playing around with setting up virtualhosts and phpmyadmin for apache2 on Ubuntu 14.04.

I notice that you are using alias php**M**y**A**dmin (not lower case phpmyadmin as you use later).

see the alias used in apache.conf

Alias /phpmyadmin /usr/share/phpmyadmin

I think this site will give you some tips ..

[https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04)

Also I have Apache 2.4.7 and I understand that I have to use this permission model in 
/etc/phpmyadmin/apache.conf
(and other virtualhost config files).

<Directory />
    AllowOverride none
    Require all denied
</Directory>

instead of

    Order Deny,Allow
    Deny from All

---

### Post by dragonfly41 on 2014-11-15
My configuration now launches from this alias 

[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by charitosha on 2014-11-17
I will need a bit of more help....
from the [link]("https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04") that you provided, i did all those steps previously.
I mean installing phpMyAdmin part. 

You also mention that something in /etc/phpmyadmin/apache.conf needs to be changed.
which exactly???
heres my /etc/phpmyadmin/apache.conf
```

# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
    Options FollowSymLinks
    DirectoryIndex index.php

    <IfModule mod_php5.c>
        AddType application/x-httpd-php .php

        php_flag magic_quotes_gpc Off
        php_flag track_vars On
        php_flag register_globals Off
        php_admin_flag allow_url_fopen Off
        php_value include_path .
        php_admin_value upload_tmp_dir /var/lib/phpmyadmin/tmp
        php_admin_value open_basedir /usr/share/phpmyadmin/:/etc/phpmyadmin/:/var/lib/phpmyadmin/
    </IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>

```

---

### Post by dragonfly41 on 2014-11-17
Your file looks just like mine ...

Changes are only necessary if you have Apache 2.4.7 and above installed.

Read more here ...

[http://httpd.apache.org/docs/trunk/upgrading.html](http://httpd.apache.org/docs/trunk/upgrading.html)

...

The only part I've changed is at the bottom ..

```

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Require all denied  
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Require all denied  
</Directory>

```

but that doesn't kick in until access to libraries or setup is requested in url.

....

near the top of /etc/apache2/apache2.conf
around line 55 ..
```

# Global configuration
#

```

add the line ...

```

# Global configuration
#
ServerName localhost

```


at the bottom of file /etc/apache2/apache2.conf I've added ...

```

Include /etc/phpmyadmin/apache.conf

```


more tips here ...

[https://github.com/jeff1evesque/LeQue/issues/387](https://github.com/jeff1evesque/LeQue/issues/387)

---

