---
title: "Cacti doesn't work"
date: 2008-05-10
forum: General Help
---

### Post by 5hark on 2008-05-10
Hello

I have just installed cacti on Ubuntu 8.04 Server. After installation i changed /etc/cacti/apache.conf as follows:

```

Alias /cacti /usr/share/cacti/site

<DirectoryMatch /usr/share/cacti/site>
        Options +FollowSymLinks
        AllowOverride All
        order allow,deny
        allow from all
#       <IfModule mod_php4.c>
                AddType application/x-httpd-php .php

#               php_flag magic_quotes_gpc Off
#               php_flag short_open_tag On
#               php_flag register_globals Off
#               php_flag register_argc_argv On
#               php_flag track_vars On
#               # this setting is necessary for some locales
#               php_value mbstring.func_overload 0
#               php_value include_path .

                DirectoryIndex index.php
#       </IfModule>
</DirectoryMatch>

```

/etc/cacti/debian.php

```

$database_username='cacti';
$database_password='********';
$basepath='';
$database_default='cacti';
$database_hostname='localhost';
$database_port='';
$dbtype='mysql';

```

```
# ls -lha /etc/apache2/mods-enabled/ |grep php
lrwxrwxrwx 1 root root   27 2008-05-10 19:13 php5.conf -> ../mods-available/php5.conf
lrwxrwxrwx 1 root root   27 2008-05-10 19:13 php5.load -> ../mods-available/php5.load

```

So it seems everything is to be ok, but when I open [http://myserver/cacti/](http://myserver/cacti/) in broser it just ask me to download file, when I saved and opened it, the contents was same as in /usr/share/cacti/site/index.php file.

I have created new file iii.php in /usr/share/cacti/site/ with following contents: 

```
<?php
phpinfo();
```
It works as expected, and shows me all available modules and other stuff.

Can anyone suggest, what can I do to make cacti works?
Thank you.

---

