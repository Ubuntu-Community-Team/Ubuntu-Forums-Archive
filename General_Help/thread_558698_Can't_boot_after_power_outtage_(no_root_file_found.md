---
title: "Can't boot after power outtage (no root file found)"
date: 2007-09-24
forum: General Help
---

### Post by AbsolutMayhem on 2007-09-24
Newbie here-
My setup was Dapper on an external USB HDD; WinXP on internal HDD. It was a real pain to set up, but I finally got it working halfway decently.

Now, after a power outtage, I can't boot to Ubuntu. Here's what I get:

[COLOR="Blue"]Booting 'Ubuntu, Kernel 2.6.15-23-386'

root (hd0,0)
Filesystem is ext2fs, partition type 0x83
Kernel /boot/umlinuz-2.6.15-23-386 root=/dev/sdal ro quiet splash
[Linux-bzImage, setup=0x1c00, size=0x15774d]
initrd /boot/initrd.img-2.6.15-23-386 
[Linux-initrd @ 0x1f942000, 0x6ad3f7bytes]
save default
boot

Uncompressing Linux...OK, booting the kernel

mount: Mounting /dev/sda1 on root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory	
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init

Busybox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)

Enter help for a list of built-in commands

/bin/sh: can't access tty: job control turned off[/COLOR]

Can anyone help??

BTW - WinXP boots with no problems

---

### Post by AbsolutMayhem on 2007-10-03
hitting escape while booting and going into safe mode doesn't help -ubuntu still can't find the root file 

Should I reinstall?

Anyone?

---

### Post by tgalati4 on 2007-10-03
Sounds like the power outage did some bad things to your USB drive.  I would do some testing on it before reinstalling.  What make is the drive?  Perhaps you can find the manufacturer's setup disk and do a low-level erase/format and some diagnostic testing.

If you can't find those utilities, you can download and burn the Ultimate Boot CD, which has utilities from several manufacturers on one disk.

---

### Post by AbsolutMayhem on 2007-10-03
I have a copy of the ultimate boot cd...

How do I boot to ubuntu from it (sorry for my ignorance)

---

### Post by tgalati4 on 2007-10-04
The Ultimate Boot CD is used to run tests on your hardware.  It's not designed as a GRUB replacement.  It contains a collection of the most popular manufacturer test utilities.  

If  you have a West Digital hard drive that is acting up, boot up the Ultimate Disk and choose the Western Digital disk diagnostic.  It will run a battery of tests (including reading the SMART codes) and give you summary of the drive's health.

Since  your drive is USB, you may have to remove it from its enclosure and place it on the IDE ribbon cable.  Most of these utilities will only work on IDE drives since the SMART diagnostic codes are only readable from the IDE bus.

You can boot Ubuntu using a Live Dapper CD and do:

>sudo fsck /dev/sda1

That will check the drive's file system and attempt to repair damage.  If the drive has a physical problem, I would try to recover data from it first.  Use the Live CD to mount the disk and start copying important files (/home/yourstuff) to a flash disk.  You may not get a second chance.  Failing drives tend to only work for a short time after the first crash.

---

