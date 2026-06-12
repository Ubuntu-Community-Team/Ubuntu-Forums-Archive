---
title: "Can't mount a partition, help plaese."
date: 2007-09-01
forum: General Help
---

### Post by HGodzillov on 2007-09-01
Well, I'm still a newb with Ubunutu (6.06), and I couldn't manage this problem. I have two hard drives, the first one, 30 GB is with XP installed on it and the other is devided - the first partition is for the Ubuntu system, and the other (10 GB) I still cannot mount. Following [this]("https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html") instruction I successfully mounted the XP drive (30 GB). But when I tried to imly it to the 10 GB partitions, it didn't mounted. 
Can somebody help, please?

---

### Post by meierfra on 2007-09-01
Please post the output of

```
cat /etc/fstab
```
and
```
sudo fdisk -l 
```
( The  l is a lower case L)

---

### Post by HGodzillov on 2007-09-01
The result from the first one:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/windows ntfs umask=0222 0 0
/dev/hdc1 /media/hard vfat umask=0000
ra@ra-desktop:~$


and the from the second:
> Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3737    30017421    7  HPFS/NTFS

Disk /dev/hdc: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1304    10474348+   c  W95 FAT32 (LBA)
/dev/hdc2   *        1305        2445     9165082+  83  Linux
/dev/hdc3            2446        2498      425722+   5  Extended
/dev/hdc5            2446        2498      425691   82  Linux swap / Solaris



---

### Post by HGodzillov on 2007-09-01
Up

---

### Post by merlinus on 2007-09-01
From what I see, the first partition on your second hdd is fat32, and the second is linux.  Both are referenced in /etc/fstab, so you need to more explicit about what you are wanting.

There are no other partitions except /swap on that hdd, according to results of sudo fdisk -l.

-merlin

---

### Post by vanadium on 2007-09-01
You should be able to see the contents of your fat32 partition navigating with nautilus to /media/hard

---

### Post by HGodzillov on 2007-09-01
Well, I'm talking about that first partition, it is 10 GB, also is displayed in the Computer window, but I don't have access to it, because it is not mounted.

---

### Post by HGodzillov on 2007-09-01
> **vanadium said:**
> You should be able to see the contents of your fat32 partition navigating with nautilus to /media/hard
Yes I see it but just as a folder.

When I enter in the Computer window I have Filesystem( where are the system files), windows volume 28 GB, floppy, cd-rw, and a 10.0 GB volume (this is hdc1), to which I don't have access, because it is not mounted

---

### Post by merlinus on 2007-09-01
You might try changing the applicable line in /etc/fstab to:

/dev/hdc1 /media/hard vfat iocharset=utf8,umask=000 0 0

-merlin

---

### Post by HGodzillov on 2007-09-01
I changed this line, merlinus, but still no success. When I click on the icon/show more details of the partition it says : mount: only root can mount /dev/hdc1 on /media/hard
Don't know if this info can help.

---

### Post by vanadium on 2007-09-01
This suggests that indeed your fat volume is not mounted. To make sure, type "mount" at the command prompt. /dev/hdc1 will not be in the list. Alternatively, "mount | grep hdc1" will yield no output).

According to your fstab, the volume should be mounted at boot time,  Are you having error messages during startup? What messages do you get when typing "sudo mount -a" at the prompt (this reloads /etc/fstab, and if one of the mounts does not succeed, you will have an error message)? 

It might be related to your fat volume being faulty. In order to check and correct this, you can run doschk (the chkdsk of Linux). We have had an erroneously behaving fat32 formatted USB stick cured after checking the file system here [http://ubuntuforums.org/showthread.php?t=537407](http://ubuntuforums.org/showthread.php?t=537407)

---

### Post by HGodzillov on 2007-09-01
vanadium, the command 
> sudo mount -a
gives the following result
> mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I'll try the link you gave to me now :)

---

### Post by HGodzillov on 2007-09-01
Still no breakthrough :(

---

### Post by merlinus on 2007-09-01
Boot into windows and run chkdsk on the drive (whatever letter windows calls it) with the /f parameter.

Then boot back into ubuntu.

-merlin

---

### Post by HGodzillov on 2007-09-01
I'm affraid that drive is quite old (this may be the answer to why it didn't mount) and I'm not sure if it will survive the disk check. However, if you have any other ideas how to mount it, please share them.

---

### Post by merlinus on 2007-09-01
If the disk has errors, ubuntu will not mount it.

-merlin

---

### Post by vanadium on 2007-09-02
You do not have to use Windows to check the disk. Linux has dosfsck (sorry, typed erroneously doschk in my earlier post) to check and repair fat volumes. However, it might well be that also dosfsck will not be able to make anythng from your drive, as it is not recognised as a fat system in the first place. Sure it is a fat volume? Run "sudo fdisk -l" to make sure the system sees the volume (drive and partitions shouldbe listed), and whether the system sees it is fat. If it is not a fat volume, the fstab entry is wrong. If it is a fat volume, try checking it with the command

dosfsck /dev/hdc1

This will check the volume and report errors. 

Adding the -a option will automatically repair.

---

