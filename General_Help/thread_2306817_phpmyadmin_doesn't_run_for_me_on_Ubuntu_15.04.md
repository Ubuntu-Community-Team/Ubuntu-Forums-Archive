---
title: "phpmyadmin doesn't run for me on Ubuntu 15.04"
date: 2015-12-19
forum: General Help
---

### Post by mbk2 on 2015-12-19
I have installed Apache2, MySQL 5.6, PHP5 on my laptop and all they are working properly.
When I install phpmyadmin I get this strange message when accesing localhost/phpmyadmin:

**Fatal error**:  Call to undefined function __() in **/usr/share/phpmyadmin/libraries/core.lib.php** on line [B]235


[/B]I am now looking for a solution to access phpmyadmin for a week right now,  googled around, I de-installed and installed
all aplications but I didn't found a way to acces this. Can anyone help me?


My environment is:

**Ubuntu 15.04 64-bit**

[B]Apache server running
Server version: Apache/2.4.10 (Ubuntu)[/B]
Server built:   Jul 24 2015 17:25:18
&#9679; apache2.service - LSB: Apache2 web server
   Loaded: loaded (/etc/init.d/apache2)
   Active: active (running) since sáb 2015-12-19 08:35:36 CET; 14min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1596 ExecStart=/etc/init.d/apache2 start (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/apache2.service
           &#9500;&#9472;1651 /usr/sbin/apache2 -k start
           &#9500;&#9472;1654 /usr/sbin/apache2 -k start
           &#9500;&#9472;1655 /usr/sbin/apache2 -k start
           &#9500;&#9472;1656 /usr/sbin/apache2 -k start
           &#9500;&#9472;1657 /usr/sbin/apache2 -k start
           &#9500;&#9472;1658 /usr/sbin/apache2 -k start
           &#9492;&#9472;2253 /usr/sbin/apache2 -k start

dic 19 08:35:35 XXX systemd[1]: Starting LSB: Apache2 web server...
dic 19 08:35:35 XXX apache2[1596]: * Starting web server apache2
dic 19 08:35:35 XXX apache2[1596]: AH00558: apache2: Could not reliably determine the server's fully qualified domain n...message
dic 19 08:35:36 XXX apache2[1596]: *
dic 19 08:35:36 XXX systemd[1]: Started LSB: Apache2 web server.
Hint: Some lines were ellipsized, use -l to show in full.


**MySQL 5.6** 
mysql  Ver 14.14 Distrib 5.6.27, for debian-linux-gnu (x86_64) using  EditLine wrapper
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: active (running) since sáb 2015-12-19 08:35:31 CET; 15min ago
  Process: 820 ExecStartPost=/usr/share/mysql/mysql-systemd-start post (code=exited, status=0/SUCCESS)
  Process: 813 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 819 (mysqld_safe)
   CGroup: /system.slice/mysql.service
           &#9500;&#9472; 819 /bin/sh /usr/bin/mysqld_safe
           &#9492;&#9472;1175 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --log-error=/var/log/mysql/...

dic 19 08:35:30 XXX systemd[1]: Starting MySQL Community Server...
dic 19 08:35:30 XXX mysqld_safe[819]: 151219 08:35:30 mysqld_safe Can't log to error log and syslog at the same time.  ...effect.
dic 19 08:35:30 XXX mysqld_safe[819]: 151219 08:35:30 mysqld_safe Logging to '/var/log/mysql/error.log'.
dic 19 08:35:30 XXX mysqld_safe[819]: 151219 08:35:30 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
dic 19 08:35:31 XXX systemd[1]: Started MySQL Community Server.
Hint: Some lines were ellipsized, use -l to show in full.

**PHP5**
PHP 5.6.16-2+deb.sury.org~vivid+1 (cli) 
Copyright (c) 1997-2015 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2015 Zend Technologies
    with Zend OPcache v7.0.6-dev, Copyright (c) 1999-2015, by Zend Technologies
PhP5 is installed. Checked with phpinfo and it works although in my phpinfo
isn't listed the mysql, mysqli and mysqld whereas it is defined in php.ini?

**phpmyadmin** 4:4.2.12-2+deb8u1build0.15.04.1

---

### Post by dragonfly41 on 2015-12-19
I don't know why you have that error message.

For my own localhost development I've installed phpMyAdmin as a virtualhost site on apache2 .. and placed the downloaded phpMyAdmin source into /var/www/phpmyadmin.dev/

I created a virtualhost site named phpmyadmin.dev and placed phpmyadmin.dev.conf in /etc/apache2/sites-available

I added phpmyadmin.dev to /etc/hosts .. reboot Ubuntu.

I can then enable/disable that virtual host (as other virtualhosts) .. [http://phpmyadmin.dev/](http://phpmyadmin.dev/)

However I do have a redundant copy of phpMyAdmin under /usr/share/

I believe this is a legacy of installing phpMyAdmin as a Ubuntu package.

---

### Post by mbk2 on 2015-12-19
thanX for your reply.
I will test this ASAP and let you know if it worked.

---

### Post by dragonfly41 on 2015-12-19
I did find an answer to your original question here ..

[http://stackoverflow.com/questions/21261825/phpmyadmin-cant-run-on-centos-6-5-with-php5-5-8](http://stackoverflow.com/questions/21261825/phpmyadmin-cant-run-on-centos-6-5-with-php5-5-8)

[http://stackoverflow.com/questions/21243704/call-to-undefined-function-error-phpmyadmin](http://stackoverflow.com/questions/21243704/call-to-undefined-function-error-phpmyadmin)

solution proposed .. session directory must be writable.

...


If you setup as virtualhost (as I suggesated) check that you apply www-data ownership to the virtualhost files.

---

### Post by mbk2 on 2015-12-20
Hmm - I am sorry.
I did exactly what you proposed but it didn't help.
The links you send me brought also no solution (I have tried this before).
The same result.
When accessing now my virtual host phadmin.dev I get the same error: **Fatal error**:  Call to undefined function __() in **/var/www/phpadmin.dev/libraries/core.lib.php** on line [B]235


[/B]

---

### Post by dragonfly41 on 2015-12-20
Let's focus on the virtualhost you have just configured.
I assume from your post above that you have chosen to name it phpadmin.dev and not phpmyadmin.dev

More general advice here.

[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)

Also reading here ..

[http://stackoverflow.com/questions/26558629/fatal-error-call-to-undefined-function-in-phpmyadmin](http://stackoverflow.com/questions/26558629/fatal-error-call-to-undefined-function-in-phpmyadmin)

> Check that your session directory is writable by the webserver process.

The best way to do so is to create your own phpinfo file; in any web accessible folder create a file (you can call it test.php or phpinfo.php or whatever you'd like) with the following content:

```

<?php
phpinfo();
?>

```

Open that file in your browser ([http://localhost/test.php](http://localhost/test.php) or similar) and look for the line session.save_path. That's your session folder; make sure the permissions are suitable and see if that helps.


Another suggestion in above thread is to check that you have PHP5 JSON module installed.

Read more here ... [http://askubuntu.com/questions/624017/php-fatal-error-call-to-undefined-function-triggered-by-different-apps](http://askubuntu.com/questions/624017/php-fatal-error-call-to-undefined-function-triggered-by-different-apps)


And finally check your virtualhost status by running command

**apache2ctl -S**

[http://www.faqforge.com/linux/controlpanels/get-a-list-of-all-virtual-hosts-which-are-defined-in-all-apache-configuration-files/](http://www.faqforge.com/linux/controlpanels/get-a-list-of-all-virtual-hosts-which-are-defined-in-all-apache-configuration-files/)


You can create a simple phpinfo.php file at your virtualhost DocumentRoot

/var/www/phpadmin.dev/phpinfo.php

---

### Post by mbk2 on 2015-12-20
php info works!
I assume there must be something with my MySQL installation?
TbH seeing this I don't know what to do:

when installing (or trying): sudo get-apt install php5-* (following the [link]("http://askubuntu.com/questions/624017/php-fatal-error-call-to-undefined-function-triggered-by-different-apps")) 

php5 is already the newest version.
php5-cli is already the newest version.
php5-gd is already the newest version.
php5-gd set to manually installed.
libapache2-mod-php5 is already the newest version.
libapache2-mod-php5 set to manually installed.
php5-common is already the newest version.
php5-common set to manually installed.
php5-json is already the newest version.
php5-mcrypt is already the newest version.
php5-mcrypt set to manually installed.
php5-mysqlnd is already the newest version.
php5-readline is already the newest version.
php5-readline set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libapache2-mod-php5 : Conflicts: libapache2-mod-php5filter but 5.6.16+dfsg-2+deb.sury.org~vivid+1 is to be installed
 libapache2-mod-php5filter : Conflicts: libapache2-mod-php5 but 5.6.16+dfsg-2+deb.sury.org~vivid+1 is to be installed
 php5-apcu : Conflicts: php5-user-cache
             Conflicts: php5-xcache but 3.2.0-1build1 is to be installed
             Conflicts: php5-yac but 0.9.2-1build1 is to be installed
 php5-mysql : Conflicts: php5-mysqlnd but 5.6.16+dfsg-2+deb.sury.org~vivid+1 is to be installed
 php5-mysqlnd : Conflicts: php5-mysql but 5.6.16+dfsg-2+deb.sury.org~vivid+1 is to be installed
 php5-xcache : Conflicts: php-apc
               Conflicts: php5-user-cache
 php5-yac : Conflicts: php-apc
            Conflicts: php5-apcu but 4.0.10-1+deb.sury.org~vivid+2 is to be installed
            Conflicts: php5-user-cache
            Conflicts: php5-xcache but 3.2.0-1build1 is to be installed
E: Unable to correct problems, you have held broken packages.


I am thinking to uninstall MySQL, PHP5 and PHPmyadmin, but the last time I did it there were some "old" configurations left somewhere
that interfered in my "new" installation. This was the reason I installed this 2strtange" MySQL version.

---

### Post by dragonfly41 on 2015-12-20
Reading through your phpinfo output

what is in this line .. [COLOR=#000000]*session.save_path*[/COLOR]

---

### Post by dragonfly41 on 2015-12-20
I've used Synaptic Package Manager .. in Ubuntu 14.04 .. to compare with your "unmet dependencies" report ..

My installation report from Synaptic Package Manager ...

libapache2-mod-php5        installed
libapache2-mod-php5filter  not installed

php5-apcu    not installed
php5-user-cache    not seen in list

php5-xcache    not installed
php5-yac       not seen in list

php5-mysql   installed
php5-mysqlnd  not installed

php5-acp not listed

So there is something odd in your packages .. you might be using a more up to date installation in Ubuntu 15.04.

e.g. here is reference to php5-yac in 15.04 .. [https://launchpad.net/ubuntu/vivid/+package/php5-yac](https://launchpad.net/ubuntu/vivid/+package/php5-yac)

and php-apc here .. [https://www.howtoforge.com/apc-php5-apache2-debian-etch](https://www.howtoforge.com/apc-php5-apache2-debian-etch)

So I don't think that my 14.04 installation will help you.

Install Synaptic Package Manager in 15.04 and look through your installed packages.

...

My best guess from above information is that you have a caching problem .. so again check your session folder is writeable as suggested earlier.
My *session.save_path* is .. /var/lib/php5

---

### Post by dragonfly41 on 2015-12-20
Reading more about this .. from your first post you have Zend OPCache installed..

> [COLOR=#000000]PHP 5.6.16-2+deb.sury.org~vivid+1 (cli) [/COLOR]
[COLOR=#000000]Copyright (c) 1997-2015 The PHP Group[/COLOR]
[COLOR=#000000]Zend Engine v2.6.0, Copyright (c) 1998-2015 Zend Technologies[/COLOR]
[COLOR=#000000]with Zend OPcache v7.0.6-dev, Copyright (c) 1999-2015, by Zend Technologies[/COLOR]

It appears that Zend OPCache might conflict with php5-apcu

[https://github.com/owncloud/core/issues/14175](https://github.com/owncloud/core/issues/14175)

So try purging php5-apcu

  sudo apt-get purge php5-apcu

---

### Post by mbk2 on 2015-12-20
I think it was not the best solution but I replaced Ubuntu 15 by Ubuntu 14.
I installed everything from scratch and there was no issue - everything works fine.
I lost completely the general view and I think without willing it I had some corrupted installations.

Thank you very much for your invested time - I am sorry not to have solved it following all your tips.


Will close this thread - if I find the way how.

---

### Post by dragonfly41 on 2015-12-20
I don't have 15.04 installed so the errors you reported were puzzling.
They did seem to relate to Zend extension.

> [COLOR=#000000]Will close this thread - if I find the way how.[/COLOR]
Go to "thread tools" at top of this page.

---

