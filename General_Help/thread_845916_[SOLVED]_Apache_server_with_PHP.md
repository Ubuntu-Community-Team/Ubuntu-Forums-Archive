---
title: "[SOLVED] Apache server with PHP"
date: 2008-07-01
forum: General Help
---

### Post by ceclauson on 2008-07-01
Hello!

I'm trying to get the Apache server working on my machine with PHP.  I've installed the server, and it serves html pages out of the htdocs directory, but when I put PHP files there and http them, my web browser just offers to download them.

I read this tutorial:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
and got all of the packages it recommended, but the problem is the same.

Am I supposed to be putting PHP files in a different directory?

Thanks
Cooper

---

### Post by leg on 2008-07-01
It sounds like you don't have the php module installed. Install it from synaptic and you should be ok. Can't remember what it is called but it is probably something like modphp.

---

### Post by ceclauson on 2008-07-01
Thanks for your reply.

The link I posted above says to install the packages apache2 libapache2-mod-php5 php5-mysql and mysql-server to get a LAMP system going, and I've done that.

(edit)

Just in case anyone else has this problem...

I found some helpful info here:
[http://www.linuxforums.org/servers/setting_up_a_server.html](http://www.linuxforums.org/servers/setting_up_a_server.html)

Apparently
(1) PHP scripts that you would like to serve are supposed to be in /var/www/
(2) the httpd.config file has to contain the line
```

LoadModule php5_module "/usr/lib/apache2/modules/libphp5.so"

```
where /usr/lib/apache2/modules/libphp5.so is actually where this line says it is.

However, I haven't been able to test this due to a new problem I'm having with Apache and have posted on a different thread :-(

(edit)

I got my server working again, but it won't serve PHP scripts from /var/www/ at all.  If anyone has any ideas, they would be much appreciated.

---

### Post by indytim on 2008-07-01
If you get to the point where you want to un-install and re-install LAMP, after you have un-installed the component parts:
```

$ sudo tasksel

```

In my opinion, it just doesn't get much easier than that!

IndyTim

---

### Post by justleen on 2008-07-01
how do you enter php mode in a file? <?  ?>  or <?php  ?>
If the first then try the latter..

---

### Post by Master Chief on 2008-07-01
**Step 1** - checking loaded modules:

```
apache2ctl -t -D DUMP_MODULES
```

Look for: php5_module

**Step 2** - testing PHP:

Save the following lines as: /var/www/index.php

```

<?php
phpinfo();
?>

```

Open your browser and enter: [http://localhost/index.php](http://localhost/index.php)

Note: Assuming you haven't changed the ServerRoot yet!

**Possible problems**

1 - PHP5 Modules not being loaded

```
sudo /usr/sbin/a2enmod php5 && sudo invoke-rc.d /etc/init.d/apache2 force-reload
```

Note: removing modules should be done with: /usr/sbin/a2dismod
      Just enter the command and that should list the loaded modules ;)

2 - Getting text instead of the info?

You can solve this by checking: /etc/apache2/mods-available/php5.conf

```

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .html .conf .txt .h
  AddType application/x-httpd-php-source .phps
</IfModule>

```

This enables the formentioned file extensions to be parsed by the PHP5 module.

---

### Post by Master Chief on 2008-07-01
> **ceclauson said:**
> 
the httpd.config file has to contain the line
```

LoadModule php5_module "/usr/lib/apache2/modules/libphp5.so"

```
where /usr/lib/apache2/modules/libphp5.so is actually where this line says it is.

Please don't!  Apache2 is different, and a lot easier to setup. Just enter 
```
sudo /usr/sbin/a2enmod
```

This will list all available modules. You can pick one and it will add the symbolic link for you. Restart Apache (see my previous post) and you're done!

Just check */etc/apache2/mods-enabled* and there you should see two symbolic links being: /etc/apache2/mod-available/php.[conf/load]

---

### Post by ceclauson on 2008-07-03
Okay, I'm not sure exactly what all I did, but PHP seems to be working now.  Thanks everyone for your responses.

-Cooper

---

