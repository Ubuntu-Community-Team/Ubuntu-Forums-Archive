---
title: "Mounting Hard Drives"
date: 2008-01-21
forum: General Help
---

### Post by alexscott on 2008-01-21
So I've got 3 hard drives in my computer.  One with linux, two for data storage.  The two for data storage are no where to be seen, I don't even know how to go about mounting them.  HELP?
I'm a little new to this, so don't get too complicated on me please? :)
Thanks in advance!

---

### Post by harlan on 2008-01-21
To mount a device:
1- $sudo fdisk -l  (with this you'll see the devices you have)
2- $sudo mkdir /media/dev1   (this creates a folder in which the device will be mounted)
3- $sudo mount -t vfat /dev/hdb1 /media/dev1   (this mount the device hdb1 in /media/dev1. In this case the filesystem is vfat, the most common in external devices, but if yours is other change it for ext3, reiserfs,...)

---

### Post by cmnorton on 2008-01-21
You have to create a physical mount point, and edit /etc/fstab to reflect the mount point. To demonstrate, I'll use one of my own systems:

lrwxrwxrwx 1 root root    6 2007-06-19 11:37 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-06-19 11:37 cdrom0
drwxr-xr-x 2 root root 4096 2007-07-02 10:28 linux_image
drwxr-xr-x 7 root root 4096 2007-11-01 08:34 sdb1

As root, I created sdb1 under /media.

Offhand, I do not know what nomenclature would be used to describe your third drive, because I do not know the configuration of your system. My drives are /dev/sda1 and /dev/sdb1, because they are both primary drives. My guess is one of your drives, #2 or #3, probably has a designator like /dev/sdb2, but you'd have to post more about your system and the drive types, and let someone else who knows more answer that part.

I edited /etc/fstab to get the drive to mount automatically:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=ec94d7ad-6480-443f-bbe7-44c6fa1e2e96 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=5b16941c-1903-426b-9375-afc5e60ccadc none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1 /media/sdb1 ext3 defaults,errors=remount-ro 0 1

Please note that /dev/sdb1, my second drive, is being mounted in /media/sdb1.

Before you reboot, you can enter sudo mount -a, and your drive should mount.

---

