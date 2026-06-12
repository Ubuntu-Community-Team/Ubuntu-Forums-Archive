---
title: "[SOLVED] /dev/hda1 has been mounted 23 times without being checked; check forced"
date: 2007-07-11
forum: General Help
---

### Post by chio on 2007-07-11
Every so often, usually every couple of weeks or so, I get the above message during the startup of my computer and I have to wait an interminable ten minutes for it to "force my check" or whatever it's doing. Sod's law dictates that it's usually just before I've got to go out, when I want to quickly boot up to check an address or something. 

I'm aware that with Linux, you can customise pretty much everything, so it's a little disingenuous for it to tell me I can't use my own computer until it's finished doing something. I'm not that bothered about the data on this computer, I'm not running a bank or anything and besides, all my important stuff is backed up over the network on a separate machine. 

To cut a long story short, since I've already got contingency in place for data loss, I'd rather have a quick startup than this long enforced wait. Is there some way to either remove this check or make it only come on every 65535 boots... anything? 

:KS

---

### Post by kevinlyfellow on 2007-07-11
You shouldn't do this, and if you do make sure you back up your data (there, now that that is said, if your fs gets mucked up, it won't be my fault!)

Open up /etc/fstab and locate the line for your root partition.  Change the last number (the 6th column) to zero.  If you don't know fstab, read this site [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by confused57 on 2007-07-11
Here is another option:
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by kevinlyfellow on 2007-07-11
Listen to confused57 and not me! ;-)

---

### Post by chio on 2007-07-11
> **confused57 said:**
> Here is another option:
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

I've done this and changed it to 100. Cheers, you're a star :KS

---

### Post by confused57 on 2007-07-11
> **chio said:**
> I've done this and changed it to 100. Cheers, you're a star :KS
Good to know it worked...I bookmarked the thread, planning on changing fsck checks on my pc, just haven't gotten around to doing so.

---

### Post by burt_57 on 2007-07-26
> **chio said:**
> Every so often, usually every couple of weeks or so, I get the above message during the startup of my computer and I have to wait an interminable ten minutes for it to "force my check" or whatever it's doing. Sod's law dictates that it's usually just before I've got to go out, when I want to quickly boot up to check an address or something. 

I'm aware that with Linux, you can customise pretty much everything, so it's a little disingenuous for it to tell me I can't use my own computer until it's finished doing something. I'm not that bothered about the data on this computer, I'm not running a bank or anything and besides, all my important stuff is backed up over the network on a separate machine. 

To cut a long story short, since I've already got contingency in place for data loss, I'd rather have a quick startup than this long enforced wait. Is there some way to either remove this check or make it only come on every 65535 boots... anything? 

:KS

same problem here.

my fstab here
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=545763a8-5556-407a-93df-700715a7098e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=c87786d2-a599-4be1-8d5f-b19cf20589cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Anyway what is it checking for ?

---

### Post by dugh on 2007-08-04
It's good that there is a command line tool to disable this, but still the default behavior needs to be changed (plus it's a pain to use tune2fs if you don't know your partition names).  At least ask people yes or no before continuing with the scan.  It's horrible when you boot up your computer and need to use it now (which is usually the case) and then have to sit back and wait 10-15 minutes or whatever for the scan to complete.

Please comment or vote or whatever on this bug report if you want this behavior changed:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/22460](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/22460)

---

