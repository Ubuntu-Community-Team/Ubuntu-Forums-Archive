---
title: "php 7.2 to 8.1 Ubuntu 18.04"
date: 2022-11-11
forum: General Help
---

### Post by garyed on 2022-11-11
I have installed multiple php versions on Ubuntu 18.04 
When I type php -v in the terminal it shows php version 8.1.8 but when I use phpinfo() in Apache it shows I'm running php version 7.2
I have tried restarting Apache2 with no change. Is there some other file that needs edited to get Apache to run php 8.1 ?
Any ideas appreciated.

---

### Post by #&amp;thj^% on 2022-11-11
check if:
```
apt policy  php8.1-cli
php8.1-cli:
  Installed: 8.1.2-1ubuntu2.8
  Candidate: 8.1.2-1ubuntu2.8
  Version table:
 *** 8.1.2-1ubuntu2.8 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     8.1.2-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages


```
if not use:
```
sudo apt install php8.1-cli 

```
and restart  Apache2

---

### Post by garyed on 2022-11-11
Here's the result of the command:
> php8.1-cli:
  Installed: 8.1.12-1+ubuntu18.04.1+deb.sury.org+1
  Candidate: 8.1.12-1+ubuntu18.04.1+deb.sury.org+1
  Version table:
 *** 8.1.12-1+ubuntu18.04.1+deb.sury.org+1 500
        500 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status

I tried running the install command too & restarting Apache but nothing changed.
It just acts like Apache is not recognizing the 8.1 version even though it is installed & showing that it's running through the terminal. 
I wonder if there could be a config file in Apache that's keeping 7.2 running instead of 8.1.

---

### Post by #&amp;thj^% on 2022-11-11
Mine was easy by default:
```
**sudo update-alternatives --config php**
[sudo] password for me: 
There is only one alternative in link group php (providing /usr/bin/php): /usr/bin/php8.1
Nothing to configure.


```
Will that change it for you?
EDIT: You can also change it like:
```
sudo a2dismod php7.2 // disable
sudo a2enmod php8.1  // enable
```

---

### Post by garyed on 2022-11-11
Now I've really messed things up. 
I ddid the: > sudo a2dismod php7.2 // disable
sudo a2enmod php8.1  // enable 
back & forth & now php is not even working at all.
All my php code just comes out plain text in my browser. It's been working fine for years. 
Anybody know how I can get it back working. 
Here's  what it looks like in the terminal:
> There are 5 choices for the alternative php (providing /usr/bin/php).

  Selection    Path             Priority   Status
------------------------------------------------------------
  0            /usr/bin/php8.1   81        auto mode
  1            /usr/bin/php5.6   56        manual mode
* 2            /usr/bin/php7.2   72        manual mode
  3            /usr/bin/php7.4   74        manual mode
  4            /usr/bin/php8.0   80        manual mode
  5            /usr/bin/php8.1   81        manual mode

I restarted Apache multiple times & even rebooted to no avail.

---

### Post by #&amp;thj^% on 2022-11-11
> **garyed said:**
> 
Anybody know how I can get it back working. 

EDIT: We need to set it now:
```
sudo update-alternatives --config php
sudo update-alternatives --config phar
sudo update-alternatives --config phar.phar

```
If no love see below
Can you show us this please:
```
 php -S localhost:8888
```
something like this:
```
[Fri Nov 11 12:20:19 2022]** PHP 8.1.2-1ubuntu2.8 Development Server** (http://localhost:8888) started

```

---

### Post by garyed on 2022-11-11
I jumped the gun & over reacted. 
Whatever I did at one point must have disabled php but I ended up fixing it & didn't think to clear my history. 
Now it's back up & working but what's weird is my phpinfo in Apache & my php -v still don't jive. 
Now my terminal command shows I'm running php 7.2 & Apache shows I'm running php 8.1

>  php -S localhost:8888
PHP 7.2.34-32+ubuntu18.04.1+deb.sury.org+1 Development Server started at Fri Nov 11 14:40:10 2022
Listening on [http://localhost:8888](http://localhost:8888)
Document root is /etc/apache2

and phpinfo() in Apache starts out like this:
> 
PHP logo
PHP Version 8.1.12
System	Linux gary 4.15.0-196-generic #207-Ubuntu SMP Thu Oct 27 21:24:58 UTC 2022 x86_64
Build Date	Oct 28 2022 17:39:18
Build System	Linux
Server API	Apache 2.0 Handler
Virtual Directory Support	disabled
Configuration File (php.ini) Path	/etc/php/8.1/apache2
Loaded Configuration File	/etc/php/8.1/apache2/php.ini
Scan this dir for additional .ini files	/etc/php/8.1/apache2/conf.d
It's actually reversed from how it was when I started this thread because it was showing 8.1 in the terminal & 7.2 in Apache.

---

### Post by #&amp;thj^% on 2022-11-11
I'm not sure about reports of version diffs, but what your after looks good now:
```
Server API Apache 2.0 Handler
Virtual Directory Support disabled
Configuration File (php.ini) Path /etc/php/8.1/apache2
**_Loaded Configuration File /etc/php/8.1/apache2/php.ini_**
Scan this dir for additional .ini files /etc/php/8.1/apache2/conf.d 
```

---

### Post by garyed on 2022-11-11
I'm just confused as to why my terminal says I'm running php7.2 when Apache says I'm running php8.1. 
The reason I'm so concerned about this is because my webhost is going to a minimum of php 8 & some of my web pages don't work under php 8.x 
They work fine on my server so I'm trying to be sure i am running php 8.x so I can test them properly.

---

### Post by garyed on 2022-11-11
php 8.1 is running fine except Phpmyadmin is not working now.
If it's not one thing it's another :)

---

### Post by garyed on 2023-02-07
Just a little update:
When I upgraded from Ubuntu Desktop 18.04 to 22.04 phpmyadmin started working again.

---

