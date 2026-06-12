---
title: "Apache/Ubuntu/Symbolic Link? issue"
date: 2013-03-07
forum: General Help
---

### Post by barraclm on 2013-03-07
[COLOR=#536482][FONT=Verdana][COLOR=#333333][FONT=courier new]I have run out of space in the partition that holds my document root (/var/www) and have moved the contents of /var/www to /home/michael/www (which is on a different partition). I then deleted /var/www and created a symbolic link in /var called www which points to /home/michael/www. This all works and I can see the files just fine (directory listings are provided below).

After reviewing many other posts, I believe that I have all the correct permissions (see below) and appropriate entries in my default apache2 configuration file (/etc/apache2/sites-enabled/default) for SymLinks etc and point to the new location of the document root.

Please could someone help me figure out what I am doing wrong. Thank you.


SERVER RESPONSE
===============
Forbidden
You don't have permission to access /phpinfo.php on this server.
Apache/2.2.22 (Ubuntu) Server at localhost Port 80

DIRECTORIES
===========
michael@The-Beast:/var$ ls -al
gives
lrwxrwxrwx 1 www-data www-data 17 Mar 6 23:37 www -> /home/michael/www

michael@The-Beast:/var$ cd /home/michael/www
michael@The-Beast:~/www$ ls -al
gives
drwxr-xr-x 5 www-data www-data 4096 Mar 6 21:05 .
drwx-w--w- 111 michael michael 12288 Mar 7 10:51 ..
drwxr-xr-x 33 www-data www-data 4096 Mar 5 14:59 joomladev
drwxr-xr-x 19 www-data www-data 4096 Dec 22 14:05 joomla-old
drwxr-xr-x 2 www-data www-data 4096 Mar 6 19:04 jooomlatest
-rwxr-xr-x 1 www-data www-data 23 Oct 20 20:54 phpinfo.php
-rwxr-xr-x 1 www-data www-data 970 Oct 21 11:33 robots.txt

APACHE2 ERROR LOG
=================
[error] [client 127.0.0.1] (13)Permission denied: access to /phpinfo.php denied
[error] [client 127.0.0.1] (13)Permission denied: access to /favicon.ico denied

CONFIGURATION FILE
==================
<VirtualHost *:80>
ServerAdmin webmaster@localhost

DocumentRoot /home/michael/www
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /home/michael/www/>
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

</VirtualHost>[/FONT]
[/COLOR]
[barraclm]("http://www.apachefriends.org/f/memberlist.php?mode=viewprofile&u=75675") **Posts:** 1**Joined:** 07. March 2013 12:50**XAMPP Version:** 1.8.0**Operating System:** Ubuntu 12.04[RIGHT][Top]("http://www.apachefriends.org/f/viewtopic.php?f=17&t=52971#wrap")[/RIGHT]

[/FONT][/COLOR]
[COLOR=#28313F]
[/COLOR]

---

