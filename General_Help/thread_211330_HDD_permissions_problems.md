---
title: "HDD permissions problems"
date: 2006-07-08
forum: General Help
---

### Post by Random Roadkill on 2006-07-08
I have 3 partitions on my hard disk:

Windows XP (yer, i know, sigh)
Ubuntu (dapper)
a 'swap' partition which both can access.

i set up the swap partition when i first installed ubuntu, before installing windows, to get dual boot. then mounted the 'swap' partition in /mnt/ 
i recently reinstalled ubuntu, after wrecking the nstillation. As a result ubuntu now recognises all 3 partitions automatically and can read from them. The only problem is that i cant write to them! 
I have tryed ```
gksudo nautilus
``` 
and 
```
sudo nautilus
```

but when i try to tick the permissin boxes it just imediatly unchecks them. These are the errors i get when trying to change the user and name

> ~$ sudo nautilus
Password:

** (nautilus:8515): WARNING **: Hit unhandled case 24 (Operation not permitted) in fm_report_error_setting_owner

** (nautilus:8515): WARNING **: Hit unhandled case 32 (Directory busy) in fm_report_error_renaming_file

Will i have to create another mount point by editting /etc/fstab?? 
thanks for wading through that rather lengthy post!! any help is greatly appreciated:D

---

### Post by Rui Pais on 2006-07-08
Hi,
what filesystem those partitions have?

Can you post your /etc/fstab and the output of 
```
mount
```

---

### Post by Random Roadkill on 2006-08-17
oops...i completely forgot i started this thread until this week, so...

the output of ```
mount
```
```
#/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw)
/dev/hda6 on /media/hda6 type vfat (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=andy)

```

my /etc/fstab/ file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

and the filesystems:
XP FAT32
'file swap' FAT32
Ubuntu ext3

---

### Post by simoncoul on 2006-08-17
```

sudo -s
nautilus

```

will bring up nautilus window right click on the partition and you can change the premissions from root to your name.

Worked for me, not a 1337 hax0r way with the terminal, but if it's already mounted I think this is the easyiest way, hope it helps!

---

### Post by Random Roadkill on 2006-08-18
it does exactly the same as in my 1st post.
btw what does the '-s' bit do?

---

