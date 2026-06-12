---
title: "How do I verify what filesystem is used"
date: 2007-11-29
forum: General Help
---

### Post by Nosgothic1 on 2007-11-29
I have an 80GB Drive that was used in a Fedora 6 system. I have added this drive to an Ubuntu 7.10 system, and I have data that I would like to recover. I had problems mounting the drive due to LVM tags. I have wiped the tags and now I receive an error when mounting:

root@Rahab:/home/nick# mount /dev/hdc1 /mnt/tmp
mount: you must specify the filesystem type

When I look at fdisk -l output it shows:
root@Rahab:/home/nick# fdisk -l /dev/hdc

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc92fc92f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        9729    78148161   83  Linux

some articles i have seen indicate that filesystem Id 83 refers to ext2 or ext3.

When I try to mount the partition indicating the type as ext2 or ext 3 then:
root@Rahab:/home/nick# mount -t ext2 /dev/hdc1 /mnt/tmp
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@Rahab:/home/nick# mount -t ext3 /dev/hdc1 /mnt/tmp
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any help would be appreciated.

---

### Post by josesanders on 2007-11-30
GParted should tell you what the file system type is.  I've had problems with the version in the repos, so if you run into problems, you can try buring a live CD and running it off of that.

---

### Post by bingoUV on 2007-11-30
LVM is not just a tag that you can wipe. It is a whole disk management system. The partition you are trying to mount as ext3, might be an LVM partition. Gparted does not understand LVM yet, so it is useless to deal with LVM. 

Read [http://www.fedoraforum.org/forum/archive/index.php/t-64964.html](http://www.fedoraforum.org/forum/archive/index.php/t-64964.html).

---

### Post by josesanders on 2007-11-30
GParted does understand LVM.  I just used it the other day, and it recognized the file system just fine.

---

### Post by bingoUV on 2007-12-01
Where did you get your gparted from? For me, gparted 0.3.3 with libparted 1.8.6 refuses to recognize the filesystem of an LVM partition. 

The latest documentation (which is from 2006) [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm) explicitly says that it does not support LVM. Has this feature been silently introduced? What do we have to do to use it? Can we also create LVMs using gparted now?

thanks

---

### Post by josesanders on 2007-12-01
I used the latest live CD.  I think that the issue is probably that it can "see" the partition, and tell me what type of file system is in use, but it can't do anything with it, i.e. resize, delete, etc.

---

### Post by Nosgothic1 on 2007-12-02
Thank you very much. I am downloading the gparted livecd now and will hope for the best and let you know how it turns out.

---

