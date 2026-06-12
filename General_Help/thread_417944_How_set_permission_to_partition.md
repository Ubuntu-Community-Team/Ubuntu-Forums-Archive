---
title: "How set permission to partition?"
date: 2007-04-22
forum: General Help
---

### Post by Necreia on 2007-04-22
I have a (what may be) simple question.  I created two partitions named BACKUP and VMWARE, but I can't access them unless I double click on them and enter the root password.

Is there a way to release that protection so I don't have to do that every time?

---

### Post by yabbadabbadont on 2007-04-22
Assuming that they are mounted in /media, and using "daffy" as an example username, you would run:
```
sudo chown daffy:daffy /media/BACKUP
sudo chown daffy:daffy /media/VMWARE
```
After that, you should be able to create files/directories in them.

---

### Post by Necreia on 2007-04-22
Thank you VERY much!

---

### Post by Necreia on 2007-04-22
It went away when I rebooted and had to do it again.  How do I make it occur every time I start the computer?

---

### Post by yabbadabbadont on 2007-04-22
> **Necreia said:**
> It went away when I rebooted and had to do it again.  How do I make it occur every time I start the computer?

Please post the contents of your /etc/fstab file.

---

### Post by Necreia on 2007-04-22
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=de899bbe-dd68-4dd4-a782-485fc65deb28 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=AC802C9D802C6FCE /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=9428028528026718 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=fb1a05c2-ebb3-46c8-b01e-9ac61c5438a5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by yabbadabbadont on 2007-04-22
Hmmm, they aren't listed.  At least not by the names you gave above.  Are they on an external drive?  What filesystem did you use when you made them?  (i.e. ext3, reiserfs, vfat, ...)

---

### Post by Necreia on 2007-04-22
They are ext3 (VMWARE) and ext2 (BACKUP).  They are under an extended partition of /dev/sda4 as partitions /dev/sda5 (ext3, VMWARE) and partitions /dev/sda6 (ext2, BACKUP)

They are on the same SATA hard disk as all the others (there's two hard drives, /dev/sda and dev/sdb)

---

### Post by yabbadabbadont on 2007-04-22
> **Necreia said:**
> They are ext3 (VMWARE) and ext2 (BACKUP).  They are under an extended partition of /dev/sda4 as partitions /dev/sda5 (ext3, VMWARE) and partitions /dev/sda6 (ext2, BACKUP)

They are on the same SATA hard disk as all the others (there's two hard drives, /dev/sda and dev/sdb)

Try adding these two lines to your /etc/fstab file.  You will need to use sudo (or gksudo) when you edit the file.
```
/dev/sda5       /media/VMWARE           ext3        defaults                   0       2
/dev/sda6       /media/BACKUP           ext2        defaults                   1       2
```
These entries will cause both of them to be mounted during boot.  If you don't want that, change "defaults" to "user,noauto".  Then you will be able to mount them as your normal user without using sudo.

---

### Post by theolster on 2007-04-24
I've had a second hard mounted for some time now (pre feisty).  

But after a clean feisty install I'm having no end of problems, I want the drive to mount automatically at boot time, and be accessible to all users.  Here is the line in my fstab:```
/dev/hda5       /media/resources	ext2	user,auto	0	0
```The directory /media/resources exists... If I try mount -a after bootup I get this error?```
mount: /dev/hda5 already mounted or /media/resources busy
```

---

### Post by theolster on 2007-04-24
man I'm so dumb... It looks like the mount points have been moved around during Feisty install.  I should have been using hda2!  All working now though :)

---

