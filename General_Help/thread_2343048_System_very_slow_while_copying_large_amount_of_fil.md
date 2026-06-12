---
title: "System very slow while copying large amount of files"
date: 2016-11-12
forum: General Help
---

### Post by studentenfutter on 2016-11-12
Hi! 

When I copy a large amount of files between two discs Ubuntu 16.04 slows down a lot and becomes quite sluggish (for example Thunderbird takes > 20 seconds to open; when I type sometimes the text takes a few seconds to appear; task switching is very slow, browsing via Firefox is slow, etc.). When I stop the copying (I use rsync), everything is ok again.

I'm copying files between two HDDs (from sdb1 to sdc2, while on sdc1 is also my /home-directory). Is it normal that Linux slows down so much? Or is there something I could check to speed the system up a bit? 

(I'm using Ubuntu for about three months, so I don't have that much experience.)

Thanks!

---

### Post by deadflowr on 2016-11-12
It helps to know the machine specs.

---

### Post by SeijiSensei on 2016-11-12
Rsync is going to push the disks to their maximum speeds.  You should not expect anything else to be responsive while doing the copying. Loading programs will contend for access with the drives, and if your machine needs to use swap, that will be slow as well.

If you know how to schedule a cron job, set it up to do the transfers when you're not working with the machine.  For help read [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by studentenfutter on 2016-11-12
> **deadflowr said:**
> It helps to know the machine specs.

Core i5 2500k, 8GB RAM, GT960, Ubuntu is on a SSD, both harddisks are 3TB drives with 7.200rpm. I used Win7 on this PC before, and copying large files wasn't slowing the system down in that way.

> **SeijiSensei said:**
> Rsync is going to push the disks to their  maximum speeds.  You should not expect anything else to be responsive  while doing the copying. Loading programs will contend for access with  the drives, and if your machine needs to use swap, that will be slow as  well.

If you know how to schedule a cron job, set it up to do the transfers when you're not working with the machine.  For help read [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Ok, good to know that this seems to be normal. Thanks!

---

### Post by ventrical on 2016-11-12
> **studentenfutter said:**
> Core i5 2500k, 8GB RAM, GT960, Ubuntu is on a SSD, both harddisks are 3TB drives with 7.200rpm. I used Win7 on this PC before, and copying large files wasn't slowing the system down in that way.



Ok, good to know that this seems to be normal. Thanks!

Yes.. even the SATA3 HDDs are slow in comparision to SATA 3 ssd.  USB 3 can sometimes  perform faster than SATA 3 hdds>3TBs.

---

### Post by kingneutron on 2016-12-01
' nice ' and ' ionice ' programs may help with system responsiveness under I/O load, or you could try changing your I/O scheduler. (Although this is kind of advanced, could have repercussions on the system overall, and could prevent system booting if there's a typo in grub config. Use at your own risk, and make backups first.)  You should already have ionice on your system, it's provided in the util-linux package.

--Try ' nice rsync blahblahblah ', see if that makes a difference. If rsync is already running, try ' ionice -c 2 -p `pidof rsync` ' # (without the single quotes)

--More info:
[http://askubuntu.com/questions/784442/why-does-ubuntu-16-04-set-all-drive-io-schedulers-to-deadline](http://askubuntu.com/questions/784442/why-does-ubuntu-16-04-set-all-drive-io-schedulers-to-deadline)

[http://askubuntu.com/questions/78682/how-do-i-change-to-the-noop-scheduler](http://askubuntu.com/questions/78682/how-do-i-change-to-the-noop-scheduler)

--As always, please let us know what you tried and what the results were, especially if they were positive.

---

### Post by kingneutron on 2016-12-01
--Oh, if nothing else seems to be working try issuing these as root: (NOTE they will not survive a reboot unless you commit them with sysctl or put them in /etc/rc.local - TRY them before committing! )

# hopefully better multitasking I/O performance
echo 20 > /proc/sys/vm/dirty_ratio

# Try to keep at least 100MB of free RAM at all times
echo 100000 > /proc/sys/vm/min_free_kbytes

# Default 100 - try more aggressively to reclaim inodes, etc from cache
echo 160 > /proc/sys/vm/vfs_cache_pressure

--Also try mounting your filesystems with "noatime" in /etc/fstab, that will cut down on timestamp writes.

--More info:
[https://brunomgalmeida.wordpress.com/2012/04/20/speed-up-linux-io/](https://brunomgalmeida.wordpress.com/2012/04/20/speed-up-linux-io/)

---

