---
title: "DVD ROM not working correctly."
date: 2007-05-31
forum: General Help
---

### Post by DarkSim on 2007-05-31
My DVD ROM drive isn't working correctly.The drive can read CD's but every DVD I put in pops up as a blank DVD/CD Rom Disc.

I searched around the forums  for answers.I have the libdvdcss2 installed.My fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=6bacbeb0-c9bf-42e6-b3f0-2cc10d0eab46 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=3c69c93e-cd72-4a39-bfda-ce0ca73eca87 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
```


What else can I try to get the drive to read DVDs?I'm still fairly new Ubuntu.I only had it up for 10 days now.

---

### Post by DarkSim on 2007-05-31
Nevermind.I got it to work after installing Automatix and it went and  and showed some HAL packages to download in the Update Manager something like that.

---

