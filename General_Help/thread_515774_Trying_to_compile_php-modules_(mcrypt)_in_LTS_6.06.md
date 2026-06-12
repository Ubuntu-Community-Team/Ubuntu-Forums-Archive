---
title: "Trying to compile php-modules (mcrypt) in LTS 6.06.1"
date: 2007-08-02
forum: General Help
---

### Post by gamble6x on 2007-08-02
I am currently running Ubuntu Server 6.06.1 LTS Dapper. I'm trying to maintain a secure system so I do not want to open the "Universe" repo nor do I want to dist-upgrade to 6.10 or 7.04 (I really want the LTS). As such php5-mcrypt as well as several others are not available.

I would like to keep the package managed Apache2, php5, and MySql. So that the package management system can keep those up to date.

I would like to manually maintain the latest versions of mcrypt, GD2, phpMyAdmin, and Drupal.

I have installed build-essential and php5-dev from aptitude.

Starting with mcrypt I downloaded the latest Libmcrypt from sourceforge. Compiled using --disable-posix-threads (as everywhere I looked suggested this) and installed (make clean, make, make install). From there I've found a couple options, but neither seems to be available:

Either I'm supposed to go to the php source directory and run ./configure --with-mcrypt=/usr/local/lib/libmcrypt run make, and then cp the generated libmcrypt.so file to /usr/lib/php5/extension and add the extension to the php.ini file. But there is no configure in the php source directory provided by php5-dev.

OR I'm supposed to go to the <php source directory>/ext/mcrypt and run phpize and then run ./configure --with-mcrypt=/usr/local/lib/libmcrypt, make clean, make, make install from there. But there is no mcrypt folder inside the ext folder in the php source directory provided by php5-dev.

I could download the source directly from php.net, but I'm trying to make sure the source I used is exactly the same as what is actually running on the system.

So in the end I'm really asking: Running php5 from aptitude, how do I get what I need to compile additional php shared modules that are not included in the ubuntu main repo?

Thanks,
Brandon

---

