---
title: "How to install SQLITE3 UBUNTU 12.04"
date: 2013-10-13
forum: General Help
---

### Post by patdundee on 2013-10-13
Hi Guys
Does anyone have the idiots guide on how to install and activate sqlite3 on Ubuntu server 12.04 precise. I have tried many times with different suggestions without success. The latest attempt was the following
> [COLOR=#000000]$ sudo apt-get install php5-cli php5-dev make[/COLOR]
[COLOR=#000000]$ sudo apt-get install libsqlite3-0 libsqlite3-dev[/COLOR]
[COLOR=#000000]$ sudo apt-get install php5-sqlite3[/COLOR]
[COLOR=#000000]$ sudo apt-get remove php5-sqlite3[/COLOR]
[COLOR=#000000]$ cd ~[/COLOR]
[COLOR=#000000]$ wget [/COLOR][http://pecl.php.net/get/sqlite3-0.6.tgz](http://pecl.php.net/get/sqlite3-0.6.tgz)
[COLOR=#000000]$ tar -zxf sqlite3-0.6.tgz[/COLOR]
[COLOR=#000000]$ cd sqlite3-0.6/[/COLOR]
[COLOR=#000000]$ sudo phpize[/COLOR]
[COLOR=#000000]$ sudo ./configure[/COLOR]
[COLOR=#000000]$ sudo make[/COLOR]
[COLOR=#000000]$ sudo make install[/COLOR]
[COLOR=#000000]$ sudo apache2ctl restart[/COLOR][COLOR=#000000]

This workde well until ./make which errors with many lines as below
[/COLOR]/sqlite3-0.6/sqlite3.c:1557:1: error: duplicate 'static'

Also on make install which errors with many lines such as below
/sqlite3-0.6/sqlite3.c:1539:1: error: duplicate 'static'

I have checked php info and sqlite3 is enabled in the list but it does not seem to work.

Many thanks
P

---

### Post by patdundee on 2013-10-16
Has anyone got any idea on this one please?
Many thanks
P

---

### Post by oldfred on 2013-10-16
I have desktop, but python installs sqlite3 as default and all installs have python. Is it really some configuration with your php?

fred@fred-Precise:~$ sudo apt-get install sqlite3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sqlite3 is already the newest version.

Why are you not installing from repository?

---

### Post by patdundee on 2013-10-17
Hi 
I have also completed repository install and php inof shows it is included in all correct files, but sqlite still will not work After searching I found it needed dependant files which I completed in the above example, still will not work :)

---

