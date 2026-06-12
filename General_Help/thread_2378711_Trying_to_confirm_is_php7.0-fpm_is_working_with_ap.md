---
title: "Trying to confirm is php7.0-fpm is working with apache on Ubuntu 16.04"
date: 2017-11-26
forum: General Help
---

### Post by akhan3174 on 2017-11-26
Hello folks,

I configured [COLOR=#111111][FONT=Consolas]php7.0-fpm to work with apache but not sure if it is correctly configured and working.

As I understand, after installation and configuration, the output of php info file should display "[/FONT][/COLOR][COLOR=#141414][FONT=Verdana]Server API --> FPM/FastCGI" but it is still showing [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]"[/FONT][/COLOR][COLOR=#141414][FONT=Verdana]Server API --> Apache 2.0 Handler".

This is how I installed and configured [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]php7.0-fpm:

[/FONT][/COLOR]sudo apt-get install libapache2-mod-fastcgi php7.0-fpm

sudo a2enmod actions fastcgi alias

sudo a2enconf php7.0-fpm

sudo service php7.0-fpm restart

sudo systemctl status php7.0-fpm

sudo systemctl restart apache2.service

Below is the output of sudo systemctl status php7.0-fpm:

php7.0-fpm.service - The PHP 7.0 FastCGI Process Manager
   Loaded: loaded (/lib/systemd/system/php7.0-fpm.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2017-11-25 11:57:33 UTC; 23h ago
  Process: 1149 ExecStartPre=/usr/lib/php/php7.0-fpm-checkconf (code=exited, status=0/SUCCESS)
 Main PID: 1336 (php-fpm7.0)
   Status: "Processes active: 0, idle: 2, Requests: 0, slow: 0, Traffic: 0req/sec"
    Tasks: 3
   Memory: 37.8M
      CPU: 3.089s
   CGroup: /system.slice/php7.0-fpm.service
           &#9500;&#9472;1336 php-fpm: master process (/etc/php/7.0/fpm/php-fpm.conf)
           &#9500;&#9472;1340 php-fpm: pool www
           &#9492;&#9472;1341 php-fpm: pool www


Nov 25 11:57:33 ip-10-0-0-126 systemd[1]: Starting The PHP 7.0 FastCGI Process Manager...
Nov 25 11:57:33 ip-10-0-0-126 systemd[1]: Started The PHP 7.0 FastCGI Process Manager.

What I am doing wrong? Would appreciate some help and advice?

Thanks for help.

---

### Post by akhan3174 on 2017-12-13
Hello everyone,

Can I please get a response from some community members and/or Ubuntu staff on this issue?

Many thanks in advance.

---

### Post by dragonfly41 on 2017-12-13
This might offer more explanation ..

[https://www.howtoforge.com/tutorial/apache-with-php-fpm-on-ubuntu-16-04/#-installing-php-](https://www.howtoforge.com/tutorial/apache-with-php-fpm-on-ubuntu-16-04/#-installing-php-)

---

