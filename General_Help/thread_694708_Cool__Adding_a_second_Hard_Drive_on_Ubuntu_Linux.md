---
title: "Cool  Adding a second Hard Drive on Ubuntu Linux"
date: 2008-02-12
forum: General Help
---

### Post by UK-Wobbie on 2008-02-12
I have got a new hard drive what is 160GB and i am using that as the master, My old one i am using as a slave what is 80GB.

Instilled Ubuntu on the 160GB hard drive and it's not showing the slave.
But in the install menu it was showing the two hard drives. And in device manager it's showing the two master and slave, But i can not see it in computer folder.

Do any one know what is going on lol Got me a lil bit foxed :confused:

Thanks

---

### Post by Therion on 2008-02-12
Have you mounted the volume?  

Right-click on the drive in the Device Manager and select "Mount Volume".

---

### Post by iris-n on 2008-02-12
Well, possibly it's configured to automount to some specific folder, thus not appearing in the "Computer" screen. If you could type in your terminal ```
cat /etc/fstab
``` and paste here the results, we could help you out.

---

### Post by UK-Wobbie on 2008-02-12
> **iris-n said:**
> Well, possibly it's configured to automount to some specific folder, thus not appearing in the "Computer" screen. If you could type in your terminal ```
cat /etc/fstab
``` and paste here the results, we could help you out.
Here you go :)

rwaller@Ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=d97f1e90-a769-48bc-8374-f52056e3574a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=a31d0cfc-f82b-4f6d-8a8f-5046244bdcd4 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
rwaller@Ubuntu:~$

---

### Post by apetresc on 2008-02-12
> **UK-Wobbie said:**
> Here you go :)

rwaller@Ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=d97f1e90-a769-48bc-8374-f52056e3574a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=a31d0cfc-f82b-4f6d-8a8f-5046244bdcd4 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
rwaller@Ubuntu:~$
That's probably your problem: /dev/hda3 is the drive with Linux installed, and /dev/hda and /dev/hdb seem to be CD-ROM drives. There's no second hard drive mentioned here, you'll have to add it.

It's probably /dev/hdd, use ```
sudo fdisk -l /dev/hdd
``` to make sure.

---

### Post by UK-Wobbie on 2008-02-12
> **AdrianP said:**
> That's probably your problem: /dev/hda3 is the drive with Linux installed, and /dev/hda and /dev/hdb seem to be CD-ROM drives. There's no second hard drive mentioned here, you'll have to add it.

It's probably /dev/hdd, use ```
sudo fdisk -l /dev/hdd
``` to make sure.

I put in the code and it showing up this 

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00035d89

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        9729    78148161   82  Linux swap / Solaris
rwaller@Ubuntu:~$

---

### Post by apetresc on 2008-02-12
There's your problem :) Your old drive has only one partition on it -- the old swap partition. Linux obviously isn't going to mount that.

You need to use gparted to delete this old partition, create a new ext3 partition using up the entire disk, then reboot. Ubuntu should automatically detect and mount this new partition.

---

### Post by UK-Wobbie on 2008-02-12
I do not know but do i have to format the drive? As i did have Ubuntu on it. But i use a tool called Gparted to deleted the old file system. :confused:

---

### Post by UK-Wobbie on 2008-02-12
> **AdrianP said:**
> There's your problem :) Your old drive has only one partition on it -- the old swap partition. Linux obviously isn't going to mount that.

You need to use gparted to delete this old partition, create a new ext3 partition using up the entire disk, then reboot. Ubuntu should automatically detect and mount this new partition.

I give it a go thanks :)

---

### Post by apetresc on 2008-02-12
> **UK-Wobbie said:**
> I do not know but do i have to format the drive? As i did have Ubuntu on it. But i use a tool called Gparted to deleted the old file system. :confused:

Yes -- you deleted the old filesystems (except for the swap partition, you left that there), but you did not re-make them! A hard drive needs to have a filesystem installed on it to be usable, even if it doesn't have an OS on it. You need to recreate a new, blank filesystem (preferrably ext3) and then it will mount fine.
You can use gparted for that again.

---

### Post by UK-Wobbie on 2008-02-12
> **AdrianP said:**
> Yes -- you deleted the old filesystems (except for the swap partition, you left that there), but you did not re-make them! A hard drive needs to have a filesystem installed on it to be usable, even if it doesn't have an OS on it. You need to recreate a new, blank filesystem (preferrably ext3) and then it will mount fine.
You can use gparted for that again.

So deleted the old partition and then make a ext3 partition?
Do i have to format or when it shows up in Ubuntu? :confused:

Thanks for your help

---

### Post by apetresc on 2008-02-12
> **UK-Wobbie said:**
> So deleted the old partition and then make a ext3 partition?
Yes, that's what you have to do.

> Do i have to format or when it shows up in Ubuntu? :confused:
You can format the partition at the same time as when you create it. Gparted does it all for you.

> Thanks for your help
No problem :)

---

### Post by taurus on 2008-02-12
After you format/convert /dev/hdd1 from swap to ext3, you just need to add an entry in /etc/fstab

```
gksudo gedit /etc/fstab
```
at the end for it.

```
/dev/hdd1   /media/hdd1   ext3   defaults   0   1
```
Save it and then create a new mount point and mount it.

```
sudo mkdir /media/hdd1
sudo mount -a
df -h
```

---

### Post by UK-Wobbie on 2008-02-12
> **taurus said:**
> After you format/convert /dev/hdd1 from swap to ext3, you just need to add an entry in /etc/fstab

```
gksudo gedit /etc/fstab
```
at the end for it.

```
/dev/hdd1   /media/hdd1   ext3   defaults   0   1
```
Save it and then create a new mount point and mount it.

```
sudo mkdir /media/hdd1
sudo mount -a
df -h
```

Like to say thanks for all your help you lot :)
It's working fine now.

---

