---
title: "ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)"
date: 2016-01-09
forum: General Help
---

### Post by jakr2 on 2016-01-09
```
 An error occurred while installing the database:                                                               &#9474; &#9474;                                                                                                                &#9474;
 &#9474; ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)     
```
Get this when trying to install phpmyadmin im 100% certain im using the right password.

---

### Post by QDR06VV9 on 2016-01-09
Hi jakr2
[URL="https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04"]Install phpMyAdmin

[/URL]Have you set-up a password?
This error pops-up when the password has not been set-up..
You should change your root password after installation if you have not..
```
mysqladmin -u root password [newpassword]
```


Or you can change your password via
```
sudo dpkg-reconfigure mysql-server-5.5(Or your version)
```
Which will change the root password.

---

### Post by jakr2 on 2016-01-09
```
# mysqladmin -u root password *****mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

``` 

I can do [COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure mysql-server-5.5
And it works fine and lets me install phpmyadmin but when I go to mydomain.com/phpmyadmin
[/FONT][/COLOR]```

[B]Not Found
[/B][COLOR=#000000][FONT=Times New Roman]The requested URL /phpmyadmin was not found on this server.[/FONT][/COLOR]

```
I have [COLOR=#333333][FONT=UbuntuMono]Include /etc/phpmyadmin/apache.conf in [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]/etc/apache2/apache2.conf[/FONT]

[FONT=UbuntuMono]Edit: When I go to my domain/phpmyadmin it just downloads a file instead of showing me a login page. I've tried mainly every fix ive found for that problem and none has worked.[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-01-09
> **jakr2 said:**
> ```
# mysqladmin -u root password *****mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

``` 

I can do [COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure mysql-server-5.5
And it works fine and lets me install phpmyadmin but when I go to mydomain.com/phpmyadmin
[/FONT][/COLOR]```

[B]Not Found
[/B][COLOR=#000000][FONT=Times New Roman]The requested URL /phpmyadmin was not found on this server.[/FONT][/COLOR]

```
I have [COLOR=#333333][FONT=UbuntuMono]Include /etc/phpmyadmin/apache.conf in [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]/etc/apache2/apache2.conf[/FONT]

[FONT=UbuntuMono]Edit: When I go to my domain/phpmyadmin it just downloads a file instead of showing me a login page. I've tried mainly every fix ive found for that problem and none has worked.[/FONT][/COLOR]

That can happen if a config file is left over from a previous phpMyAdmin installation.
What is the output of this command:
```
ls /etc/apache2/conf.d/
```

---

### Post by jakr2 on 2016-01-09
```
ls /etc/apache2/conf.d/
ls: cannot access /etc/apache2/conf.d/: No such file or directory

```

---

### Post by QDR06VV9 on 2016-01-09
Hi I have some folks here for about 20 minutes, But in the meantime have a look here.
[http://askubuntu.com/questions/365454/apache2-error-could-not-open-configuration-file-etc-apache2-conf-d-no-such-fi](http://askubuntu.com/questions/365454/apache2-error-could-not-open-configuration-file-etc-apache2-conf-d-no-such-fi)
I will be right back to check on you;) Sorry for the slight delay..

---

### Post by jakr2 on 2016-01-09
> **runrickus said:**
> Hi I have some folks here for about 20 minutes, But in the meantime have a look here.
[http://askubuntu.com/questions/365454/apache2-error-could-not-open-configuration-file-etc-apache2-conf-d-no-such-fi](http://askubuntu.com/questions/365454/apache2-error-could-not-open-configuration-file-etc-apache2-conf-d-no-such-fi)
I will be right back to check on you;) Sorry for the slight delay..
I dont get that error my apache works fine. And thats fine, thanks for the help.

---

### Post by QDR06VV9 on 2016-01-09
> **jakr2 said:**
> ```
ls /etc/apache2/conf.d/
ls: cannot access /etc/apache2/conf.d/: No such file or directory

```
That link was for the above "**cannot access /etc/apache2/conf.d/: No such file or directory"**

> **jakr2 said:**
> I dont get that error my apache works fine. And thats fine, thanks for the help.
So is that error still present?

---

### Post by jakr2 on 2016-01-09
I dont get this error which you linked me to 
[http://askubuntu.com/questions/365454/apache2-error-could-not-open-configuration-file-etc-apache2-conf-d-no-such-fi](http://askubuntu.com/questions/365454/apache2-error-could-not-open-configuration-file-etc-apache2-conf-d-no-such-fi)
```
[COLOR=#111111][FONT=Consolas]* Starting web server apache2[/FONT][/COLOR] * The apache2 configtest failed.
Output of config test was:
apache2: Syntax error on line 263 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/: No such file or directory
Action 'configtest' failed.
``` 
My apache works fine, just phpmyadmin if I go to mydomain.com/phpmyadmin it now just downloads a file.

---

### Post by yancek on 2016-01-09
When you installed mysql, did you create a root password?  The password for mysql is not the same as the root user password.  Well, it can be but you need to set it up.

> apache2: Syntax error on line 263 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/: No such file or directory

Did you check to see what line 263 is in that file?  Is there an /etc/apache2/conf.d file?

> if I go to mydomain.com/phpmyadmin it now just downloads a file

Either php is not installed or it is not configured properly.

---

### Post by jakr2 on 2016-01-09
Yeah your right php isnt installed, but it wont install either.
```


Setting up libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.14) ...
php5_invoke pdo_mysql: already enabled for apache2 SAPI
php5_invoke json: already enabled for apache2 SAPI
php5_invoke recode: already enabled for apache2 SAPI
php5_invoke xcache: already enabled for apache2 SAPI
php5_invoke pdo: already enabled for apache2 SAPI
php5_invoke memcached: already enabled for apache2 SAPI
php5_invoke gd: already enabled for apache2 SAPI
php5_invoke mysqli: already enabled for apache2 SAPI
php5_invoke readline: already enabled for apache2 SAPI
php5_invoke pspell: already enabled for apache2 SAPI
php5_invoke intl: already enabled for apache2 SAPI
php5_invoke mysql: already enabled for apache2 SAPI
php5_invoke curl: already enabled for apache2 SAPI
php5_invoke xsl: already enabled for apache2 SAPI
php5_invoke memcache: already enabled for apache2 SAPI
php5_invoke ming: already enabled for apache2 SAPI
php5_invoke pdo_sqlite: already enabled for apache2 SAPI
php5_invoke opcache: already enabled for apache2 SAPI
php5_invoke snmp: already enabled for apache2 SAPI
php5_invoke tidy: already enabled for apache2 SAPI
php5_invoke sqlite3: already enabled for apache2 SAPI
php5_invoke imagick: already enabled for apache2 SAPI
php5_invoke xmlrpc: already enabled for apache2 SAPI
php5_invoke mcrypt: already enabled for apache2 SAPI
dpkg: error processing package libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` I have another thread about this error. Would be easier if I can re-install ubuntu but I cant do that either.

---

### Post by QDR06VV9 on 2016-01-09
A final item that we need to address is enabling the mcrypt PHP module, which phpMyAdmin relies on. This was installed with phpMyAdmin so we just need to toggle it on and restart our PHP :

```
sudo php5enmod mcrypt
sudo service php5-fpm restart
```

With that, our phpMyAdmin installation is now operational. To access the interface, go to your server's domain name or public IP address** followed by /phpmyadmin,** in your web browser:
```
http://server_domain_or_IP/phpmyadmin
```

To sign in, use a username/password pair of a valid MySQL user. The root user and the MySQL administrative password is a good choice to get started. You will then be able to access the administrative interface:

---

### Post by jakr2 on 2016-01-09
> **runrickus said:**
> A final item that we need to address is enabling the mcrypt PHP module, which phpMyAdmin relies on. This was installed with phpMyAdmin so we just need to toggle it on and restart our PHP :

```
sudo php5enmod mcrypt
sudo service php5-fpm restart
```

With that, our phpMyAdmin installation is now operational. To access the interface, go to your server's domain name or public IP address** followed by /phpmyadmin,** in your web browser:
```
http://server_domain_or_IP/phpmyadmin
```

To sign in, use a username/password pair of a valid MySQL user. The root user and the MySQL administrative password is a good choice to get started. You will then be able to access the administrative interface:
I uninstalled phpmyadmin and now it wont install again, basically nothing will install.
```


Setting up libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.14) ...
php5_invoke pdo_mysql: already enabled for apache2 SAPI
php5_invoke json: already enabled for apache2 SAPI
php5_invoke recode: already enabled for apache2 SAPI
php5_invoke xcache: already enabled for apache2 SAPI
php5_invoke pdo: already enabled for apache2 SAPI
php5_invoke memcached: already enabled for apache2 SAPI
php5_invoke gd: already enabled for apache2 SAPI
php5_invoke mysqli: already enabled for apache2 SAPI
php5_invoke readline: already enabled for apache2 SAPI
php5_invoke pspell: already enabled for apache2 SAPI
php5_invoke intl: already enabled for apache2 SAPI
php5_invoke mysql: already enabled for apache2 SAPI
php5_invoke curl: already enabled for apache2 SAPI
php5_invoke xsl: already enabled for apache2 SAPI
php5_invoke memcache: already enabled for apache2 SAPI
php5_invoke ming: already enabled for apache2 SAPI
php5_invoke pdo_sqlite: already enabled for apache2 SAPI
php5_invoke opcache: already enabled for apache2 SAPI
php5_invoke snmp: already enabled for apache2 SAPI
php5_invoke tidy: already enabled for apache2 SAPI
php5_invoke sqlite3: already enabled for apache2 SAPI
php5_invoke imagick: already enabled for apache2 SAPI
php5_invoke xmlrpc: already enabled for apache2 SAPI
php5_invoke mcrypt: already enabled for apache2 SAPI
dpkg: error processing package libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` Getting this error for lots of things, apache working fine.

---

### Post by QDR06VV9 on 2016-01-09
```
[COLOR=#111111][FONT=Consolas]sudo apt-get remove --purge [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] libapache2-mod-php5[/FONT][/COLOR]
```
Then try again to install [COLOR=#000000]*phpMyAdmin *[/COLOR]

---

### Post by jakr2 on 2016-01-09
```

Do you want to continue? [Y/n] y
(Reading database ... 220577 files and directories currently installed.)
Removing libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.14) ...
php5_invoke prerm: Disable module pdo_mysql for apache2 SAPI
php5_invoke prerm: Disable module json for apache2 SAPI
php5_invoke prerm: Disable module recode for apache2 SAPI
php5_invoke prerm: Disable module xcache for apache2 SAPI
php5_invoke prerm: Disable module pdo for apache2 SAPI
php5_invoke prerm: Disable module memcached for apache2 SAPI
php5_invoke prerm: Disable module gd for apache2 SAPI
php5_invoke prerm: Disable module mysqli for apache2 SAPI
php5_invoke prerm: Disable module readline for apache2 SAPI
php5_invoke prerm: Disable module pspell for apache2 SAPI
php5_invoke prerm: Disable module intl for apache2 SAPI
php5_invoke prerm: Disable module mysql for apache2 SAPI
php5_invoke prerm: Disable module curl for apache2 SAPI
php5_invoke prerm: Disable module xsl for apache2 SAPI
php5_invoke prerm: Disable module memcache for apache2 SAPI
php5_invoke prerm: Disable module ming for apache2 SAPI
php5_invoke prerm: Disable module pdo_sqlite for apache2 SAPI
php5_invoke prerm: Disable module opcache for apache2 SAPI
php5_invoke prerm: Disable module snmp for apache2 SAPI
php5_invoke prerm: Disable module tidy for apache2 SAPI
php5_invoke prerm: Disable module sqlite3 for apache2 SAPI
php5_invoke prerm: Disable module imagick for apache2 SAPI
php5_invoke prerm: Disable module xmlrpc for apache2 SAPI
php5_invoke prerm: Disable module mcrypt for apache2 SAPI
apache2_invoke php5 prerm: No action required
Purging configuration files for libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.14) ...
apache2_invoke php5 postrm: No action required
```
```
sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
phpmyadmin is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.
root@jakr:/#

```
No errors no more, but on mydomain.com/phpmyadmin downloads a file

---

### Post by QDR06VV9 on 2016-01-09
Now follow post #12 above again

---

### Post by jakr2 on 2016-01-09
> **runrickus said:**
> Now follow post #12 above again
I already did that

If I do ```
[COLOR=#111111][FONT=Consolas]sudo dpkg-reconfigure phpmyadmin
``` I can re-configure phpmyadmin and it works, but I still get the download on /phpmyadmin[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-01-09
[COLOR=#000000]Either php is not installed or it is not configured properly.
Please Read this again carefully
 [/COLOR][https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04)

---

### Post by jakr2 on 2016-01-09
> **runrickus said:**
> [COLOR=#000000]Either php is not installed or it is not configured properly.
Please Read this again carefully
 [/COLOR][https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04)
I've done everything on this many times.

Edit: Fixed uninstalled everything and followed this: [https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)
Just stupid mistakes, thanks for the help.

---

### Post by QDR06VV9 on 2016-01-09
**EDIT: Good Job** :D Disregard Below
You might want to mark this as solved to help others..(If you are satisfied)
Well something did not get configured right.
what is the output of
```
gedit [COLOR=#000000] /etc/apache2/conf.d [/COLOR]
```

---

