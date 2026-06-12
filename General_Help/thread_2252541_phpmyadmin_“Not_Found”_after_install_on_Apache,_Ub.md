---
title: "phpmyadmin “Not Found” after install on Apache, Ubuntu 14.04"
date: 2014-11-12
forum: General Help
---

### Post by bryan34 on 2014-11-12
[COLOR=#000000][FONT=Arial]Setting up a development environment with Ubuntu 14.04 running in VirtualBox, following this guide:[http://klau.si/dev](http://klau.si/dev)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
After installing phpmyadmin, it seems I should be able to access it at [http://localhost/phpmyadmin](http://localhost/phpmyadmin) but apache returns a Not Found error. Did this guide leave out a configuration step somewhere? 

I have already tried restarting the apache service.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
There is no phpmyadmin.conf file in apache2/sites-enabled or apache2/sites-available, is this required? [/FONT][/COLOR][COLOR=#000000][FONT=Arial]If so, where can I find these files?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Using 127.0.0.1 instead of localhost returns the same error. The default apache page at [http://localhost](http://localhost) works just fine.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The console in the browser shows nothing of value, simply Not Found.

I have also tried rerunning the install script with [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]dpkg-reconfigure -plow phpmyadmin


[/FONT][/COLOR]

---

### Post by bryan34 on 2014-11-12
This issue was resolved thanks to this guide: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_Phpmyadmin_.26_mysql-workbench](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_Phpmyadmin_.26_mysql-workbench)

by adding 

Include /etc/phpmyadmin/apache.conf

to the /etc/apache2/apache2.conf file

---

