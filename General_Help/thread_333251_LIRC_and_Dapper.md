---
title: "LIRC and Dapper"
date: 2007-01-07
forum: General Help
---

### Post by zupidupi on 2007-01-07
Hiya folks,

I'm trying to install LIRC under Dapper, with my spanking new SilverStoneTek 11M case,  specs at [http://www.silverstonetek.com/products-lc11m.htm](http://www.silverstonetek.com/products-lc11m.htm).

I follow quite closely the following guidelines (yeah, I know they are for Edgy, that might be why I'm missing something):

[http://venky.ws/forums/viewtopic.php?t=279](http://venky.ws/forums/viewtopic.php?t=279)

When I've run sudo make install I check that /dev/lirc is there, and yep, this is what I find:

misha@salemcenter:~/lirc-0.8.0/lirc$ ls -l /dev/l*
crw-r--r-- 1 root root  61, 0 2007-01-07 13:16 /dev/lirc
prw-r--r-- 1 root root      0 2007-01-07 10:49 /dev/lircd
prw-r--r-- 1 root root      0 2007-01-07 10:49 /dev/lircm
srw-rw-rw- 1 root root      0 2007-01-07 10:44 /dev/log
crw-rw---- 1 root lp     6, 0 2007-01-07 10:44 /dev/lp0
crw------- 1 root root 109, 0 2007-01-07 10:47 /dev/lvm

I do sudo modprobe lirc_dev and sudo modprobe lirc_imon, and the listing above stays the same. Then I do sudo chmod 666 /dev/lirc* - just in case! But, look at this:

misha@salemcenter:~/lirc-0.8.0/lirc$ sudo mode2
mode2: error opening /dev/lirc
mode2: No such device

And that's where I run into a wall. I don't know how to proceed, and would greatly appreciate some hints and tricks. Thx in advance,

   Mike

---

