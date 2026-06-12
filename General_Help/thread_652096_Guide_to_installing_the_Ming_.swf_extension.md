---
title: "Guide to installing the Ming .swf extension"
date: 2007-12-28
forum: General Help
---

### Post by resprung on 2007-12-28
Ming is an amazing PHP extension, which allows the server to output custom flash files.

Documentation is sparse, so here is a walkthrough of how I installed Ming as an apache dynamic extension:
===

My setup:
Ubuntu 6.06 LTS - Apache 2.0.55 - PHP v. 5.1.2


First, you need to add some "-devel" packages to attain a build environement:

install ubuntu's php-dev package
**apt-get install php5-dev**

install libfreetype-dev developer package
**apt-get install libfreetype6-dev**

install libpng12-dev developer package
**apt-get install libpng12-dev**

get a ming-copy and unpack.
in ming
[B]./configure --enable-php
make
sudo make install
cd php_ext
make[/B]

This makes your goal: the **ming.so** file.
It's in the tmp/modules dir
move ming.so -> your apache extension dir

If you're on a virtualized box, you'll need to move these 5 helper files from usr/local/lib  ->  usr/lib
**libming.a  libming.la  libming.so  libming.so.0  libming.so.0.4.0**

in php, you either call the dynamic extension from the web pages where PHP needs it:
**<? dl('ming.so'); ?>**

Or edit php.ini, adding this line:
**extension=ming.so**


Hope this helps :KS

---

