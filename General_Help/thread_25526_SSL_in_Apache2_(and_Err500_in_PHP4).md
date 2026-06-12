---
title: "SSL in Apache2? (and Err500 in PHP4)"
date: 2005-04-10
forum: General Help
---

### Post by smarttaz on 2005-04-10
How can I make SSL work in Apache2?

It always starts with '-DSSL' which I suppose means "disable SSL".

I cannot enable and load the module ssl (links to mods-available/ssl.load and ssl.conf), because Apache2 refuses to start if I try this.

Everything (openssl, etc.) seems to be installed, I cannot find anything more with Synaptic...

My Apache2 says:
Apache/2.0.53 (Ubuntu) mod_python/3.1.3 Python/2.4.1 PHP/4.3.10-10ubuntu4 mod_ssl/2.0.53 OpenSSL/0.9.7e Server at localhost Port 80

Second: Apache 2 gives Error 500 while trying to parse PHP4 files.
/var/log/apache2/error.log gives:

[error] [client 127.0.0.1] Premature end of script headers: index.php
[error] [client 127.0.0.1] Error in suphp.c on line 364: User is not allowed to run scripts

Which user? I already tried:
 sudo chown -R www-data:www-data /var/www
and was useless.

The file is simplest: <?php phpinfo(); ?>

Thx.,
[email="beranger5ca@yahoo.ca"]beranger5ca@yahoo.ca[/email]

---

### Post by smarttaz on 2005-04-10
Self-answer (maybe it shoulkd promote sometime to a howto).

[color=Red][b]A. for the SSL part, see:
[/b][/color]http://www.debian-administration.org/?article=101
[http://mario.espaciolinux.com/apache2_ssl.html]("http://mario.espaciolinux.com/apache2_ssl.html")


**[color=Red]B. for the PHP4 not working in Apache 2 under Hoary:[/color]**

MORE DETAILED DEFINITION OF THE PROBLEM:

## In /var/log/apache2/error.log:
 
 [error] [client 127.0.0.1] Premature end of script headers: index.php
 [error] [client 127.0.0.1] Error in suphp.c on line 364: User is not allowed to run scripts
 (in some other cases:
 Error in suphp.c on line 486: Group is not allowed to run scripts)
 
 ## In /var/log/suphp/suphp.log:
 
 -- For any PHP page tried:
 [error] UID of /var/www/index.php or its target (33 / www-data) < 100
 
 -- For phpMyAdmin, etc:
 [error] UID of /var/www/phpmyadmin/index.php or its target (0 / root) < 100
 [error] UID of /var/www/phpsysinfo/index.php or its target (0 / root) < 100
 
 ## Investigating...
 
 sudo /usr/lib/apache2/suexec2 -V
 we will see:
  -D AP_GID_MIN=100 
  -D AP_UID_MIN=100
 
 so... [color=Red]**our UID and GID for www-data (33) are too small!!!**[/color]
 
 
**[color=Red] SOLUTION:[/color]**
 
 #1. **Change UID and GID for user www-data** to something >100, e.g. 133.
 #2. chown -R www-data:www-data /var/www
 #3. chown -R www-data:www-data /usr/share/phpsysinfo
 #4. Note: 'fool-proof' check: make sure you have:
 chmod 750 /var/www/*.php
 
[color=Red]** UNSOLVED PROBLEM:**[/color]
 For phpMyAdmin, evem if you make:
 chown -R www-data:www-data /usr/share/phpmyadmin
 
 it will not work:
 '**Fatal error**: generic_init failed in **/usr/share/phpmyadmin/libraries/mcrypt.lib.php** on line **90**'
 
 Actually,  I guess the reason is shown by the information given by a bare :
 <? php 
 phpinfo();
 ?>
 
 The configure for the php build in this package was with:
 **'--without-mysql'**
 
 Scheisse. So phpMyAdmin will NOT work, because PHP4 will *not* work with MySQL!!!

[b]And I have php4-mysql installed, what the heck!!!!

[/b] WTF? Should I keep Hoary "for my secretary, as a desktop Linux", and try Debian Sarge for PHP development?!

---

### Post by moltar on 2005-04-20
Ya who the hell configures php with --without-mysql ... it's like releasing next version of Ubuntu without Gnome... PHP is bad enough, but without mysql it's useless

---

### Post by smarttaz on 2005-04-21
[QUOTE=moltar]Ya who the hell configures php with --without-mysql ... it's like releasing next version of Ubuntu without Gnome... PHP is bad enough, but without mysql it's useless[/QUOTE]
 
Actually, this is not the real problem.
MySQL support can be loaded as a module and it works.
 
phpMyAdmin does not work, giving me a mcrypt.c error :(

---

### Post by moltar on 2005-04-21
> MySQL support can be loaded as a module and it works.

How?

---

### Post by smarttaz on 2005-04-21
[QUOTE=moltar]How?[/QUOTE]

The lib is in my case /usr/lib/php4/20020429/mysql.so

In /etc/php4/cgi/php.ini make sure you have a line (usually at the end):
extension=mysql.so

---

### Post by jfdill_2 on 2005-05-18
[QUOTE=smarttaz]Self-answer (maybe it shoulkd promote sometime to a howto).

[color=Red][b]A. for the SSL part, see:
[/b][/color]http://www.debian-administration.org/?article=101
[http://mario.espaciolinux.com/apache2_ssl.html]("http://mario.espaciolinux.com/apache2_ssl.html")
[/QUOTE]
If you haven't been tweaking apache configuration in awhile, there are a couple vague spots in those directions.  Like it says, *and change port 80 in the name of the site to 443* but with a fresh install on Hoary there is no port 80 in the name of the site.  Also, it says to make changes *somewhere in the body of the config file*.  Color me retarded, but does *config file* refer to available-sites/ssl or apache2.conf or some other file? ](*,) I'm sure I'll figure it out, then post the answers here, but I wish I didn't have to go back to the apache2 docs to figure this out.

---

### Post by jfdill_2 on 2005-05-18
A little more detail about the "port 80" part:

In /etc/apache2/available-sites/default, you need to change the NameVirtualHost line

NameVirtualHost *:80
<VirtualHost *:80>

In /etc/apache2/available/sites/ssl (or whatever you called it)

NameVirtualHost *:443
<VirtualHost *:443>

See [Name-based Virtual Host Support](http://httpd.apache.org/docs-2.0/vhosts/name-based.html) in the apache2 docs for relevant documentation.

---

### Post by jfdill_2 on 2005-05-18
About "SSLEngine on" that goes in the virtual host def eg. available-sites/ssl (or whatever you called it).  **However** they left out one very important step, and that is that you need to link the ssl files into mods-enabled:

ln -s /etc/apache2/mods-available/ssl.conf /etc/apache2/mods-enabled
ln -s /etc/apache2/mods-available/ssl.load /etc/apache2/mods-enabled

---

### Post by ampteed on 2006-04-04
hi 
last night I and a friend scripted a php script! we runed it on his computer but when I trye to run the script on my computer nothing happens, I insert the code```
php <filename.php>
```
He says I have to sett up php with crul and sockets!
Can anyone help me with the code!

---

