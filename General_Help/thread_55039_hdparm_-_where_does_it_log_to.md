---
title: "hdparm - where does it log to?"
date: 2005-08-07
forum: General Help
---

### Post by Hamster. on 2005-08-07
Hi,

I'm trying to use hdparm to set some options on a harddrive of mine.

I've worked out the command I need by testing it out on the command line first. I then edited the /etc/hdparm.conf file and added what I need.

The problem is that the paramaters are not being set during the boot process. I'm trying to track down the cause but cannot find out where hdparm logs to!

Reading through /etc/init.d/hdparm, I see it refer to various log functions which are  defined in /lib/lsb/init-functions. I'm afraid I don't speak bash well enough though to work out which file is actually being logged to.

I've even tried grepping through all the files in /var/log for "hdparm" and other words used in the log messages, but cannot find a thing.

Can someone point me down the right path please! :-)

Thanks!

---

### Post by eivind on 2005-08-08
Hm. I thought /var/log/syslog was the way to go?

Nevertheless, you will probably see hdparm messages with

dmesg|less

but since you don't see any changes for your disks, it might just be that hdparm isn't setup to start on bootup. In that case, just do

sudo update-rc.d hdparm defaults

to have it start on bootup. See if this helps, and if it doesn't, it probably doesn't ruin anything.


Cheers,

Eivind

---

