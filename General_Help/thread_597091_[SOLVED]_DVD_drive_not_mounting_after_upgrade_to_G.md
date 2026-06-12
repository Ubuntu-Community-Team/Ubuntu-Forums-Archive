---
title: "[SOLVED] DVD drive not mounting after upgrade to Gutsy"
date: 2007-10-30
forum: General Help
---

### Post by Macros42 on 2007-10-30
I recently upgraded to Gutsty from Feisty and since then my dvd drive won't mount. It was working fine before the upgrade and it will boot from it so the drive is ok. The activity light stays on constantly and I can't eject the drive when in Gutsy. Below is some info that may help. Tried umount as well but it definitely isn't mounted. Any help is much appreciated.

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d61d19ce-3d99-47a1-8d25-eba2c4531a15 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=ba020695-e6be-4ee3-9005-8d9f0a2b866a /boot           ext2    defaults        0       2
# /dev/sda2
UUID=bf5e0ccf-2dcb-4aaa-84b7-0f50a8b5189d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

```
$ ls /dev/disk/by-uuid
ba020695-e6be-4ee3-9005-8d9f0a2b866a  bf5e0ccf-2dcb-4aaa-84b7-0f50a8b5189d  d61d19ce-3d99-47a1-8d25-eba2c4531a15
```

```
$ ls /media -l
total 4
lrwxrwxrwx 1 root root    6 2007-06-20 00:29 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-06-20 00:29 cdrom0

$ sudo mount /dev/cdrom /media/cdrom0 -t iso9660
mount: special device /dev/cdrom does not exist
```

---

### Post by Macros42 on 2007-10-31
*unashamed bump* this is driving me mad and I'm fairly new to nix - aidez moi ;)

---

### Post by dacap06 on 2007-10-31
This one has an easy fix.  The upgrade got rid of your device aliases.  Your DVD/CD device is really /dev/scd0, but most programs expect to use  the devices /dev/cdrom and /dev/dvd.  On my machine, they are merely symbolic links.  

I'll bet if you do an ls /dev/dvd you'll receive the response
ls: /dev/dvd: No such file or directory

and the same for ls /dev/cdrom.   Here's what I get on my machine::

ls -l /dev/dvd
lrwxrwxrwx 1 root root 4 2007-10-31 15:46 /dev/dvd -> scd0

ls -l /dev/cdrom
lrwxrwxrwx 1 root root 4 2007-10-31 15:46 /dev/cdrom -> scd0




So to create these devices, enter these commands (as root, or using sudo) in a termwin to create the logical links:

ln -s /dev/scd0  /dev/cdrom
ln -s /dev/scd0 /dev/dvd

---

### Post by Macros42 on 2007-10-31
Makes sense. But are your commands right? I tried them and now have:
|lrwxrwxrwx 1 root root 9 2007-10-31 23:16 /dev/cdrom -> /dev/scd0
notice the extra /dev/ that yours doesn't have. Not trying to second guess you but now I get:
"$eject cdrom
eject: tried to use `/dev/scd0' as device name but it is no block device
eject: unable to find or open device for: `cdrom'"

If that was wrong how do I remove symbolic links to retry it?

I've been doing some more research too and can't find scd0 in dmesg at all. Is that another symptom or a bigger problem?

[edit]forgetting my manners - thanks for the help :)

---

### Post by Macros42 on 2007-11-04
OK. It's all working again. Seems it was a hardware issue after all. I had booted a gentoo live cd after this problem began but today I tried it again and it wouldn't boot from cd. Took a quick look in the BIOS and the drive wasn't seen. So I reseated the drive and restarted - all ok again.

Thanks for the help.

---

### Post by dacap06 on 2007-11-04
Macros42, just got around to looking at my posts.  Glad all is well.  Congrats on the insightful hardware reseat.

BTW, to answer your questions, you can do relative symbolic links too (i.e. w/o the /dev in front of either), and it should make no difference, so long as you are in the correct directory when you make it. By using absolute paths, your working directory does not matter.

To get rid of a symbolic link, you simply remove it.  Removing a symbolic link will not delete the file it points to.

DaCAP

---

