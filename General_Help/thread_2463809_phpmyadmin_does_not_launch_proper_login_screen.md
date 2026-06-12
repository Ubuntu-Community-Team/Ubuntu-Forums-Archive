---
title: "phpmyadmin does not launch proper login screen"
date: 2021-06-18
forum: General Help
---

### Post by ccor58 on 2021-06-18
I have following versions:
php 7.4
apache2 vers 2.4.4.1
mysql server 8.0
ubuntu studio 20.04LTS 64 bit
apachectl -M  shows php module 7 (shared)
I have ensured libapache2-mod-php7.4 available and confirmed extra 'Include' added to apache2 conf file for phpmyadmin site.

When I attempt to launch it there is no icon to launch it from; and [http://localhost/phpmyadmin](http://localhost/phpmyadmin) does not seem to load the site, instead it generates 404 error  or else if it does load something it just displays html type code instead of the normal login screen. 

Any help is appreciated.
Thanx

---

### Post by norobro on 2021-06-18
Does this help? From the the file debian/README.Debian in the source code:> [COLOR=black][FONT=inherit]Should you get a 404 "not found" error when you installed phpMyAdmin using[/FONT][/COLOR][FONT=inherit]  apt-get and point your browser at <http://localhost/phpmyadmin/>.
[/FONT][FONT=inherit]
[/FONT][FONT=inherit]  Most likely you did not enable configuration for your webserver during
[/FONT][FONT=inherit]  installation. You can reconfigure phpmyadmin package to get the selection
[/FONT][FONT=inherit]  again and choose webserver you are using (eg. "Apache 2"):
[/FONT][FONT=inherit]
[/FONT][FONT=inherit]    sudo dpkg-reconfigure -plow phpmyadmin
[/FONT][FONT=inherit]
[/FONT][FONT=inherit]  You can also manually install the shipped configuration file to Apache conf.d
[/FONT][FONT=inherit]  directory (but the above way is preferred):
[/FONT][FONT=inherit]
[/FONT][FONT=inherit]    sudo a2enconf phpmyadmin
[/FONT][FONT=inherit]
[/FONT]


---

