---
title: "Udf"
date: 2006-12-10
forum: General Help
---

### Post by aco on 2006-12-10
Ubuntu 6.10 no support for UDF, is there any way i can install it?

---

### Post by riven0 on 2006-12-10
Try this in the terminal:

sudo apt-get update && sud apt-get install udftools

---

### Post by aco on 2006-12-10
Ok installed udf tools..still the same it says udf DVD and when i enter only .txt file
Should i mount or something now????

---

### Post by riven0 on 2006-12-10
> **aco said:**
> Ok installed udf tools..still the same it says udf DVD and when i enter only .txt file
Should i mount or something now????

Okay, first tell me exactly what you are trying to do, and then I can try to help from there.

---

### Post by aco on 2006-12-10
ok i just want to read my dvd that is burned in udf format
That is all, preferably i want to make udf available always, and i would like to avoid typing the commands in terminal everytime i want to read udf dvd

---

### Post by riven0 on 2006-12-10
> **aco said:**
> ok i just want to read my dvd that is burned in udf format
That is all, preferably i want to make udf available always, and i would like to avoid typing the commands in terminal everytime i want to read udf dvd

Okay, we can try mounting it. Can you post the output of fdisk -l here?

---

### Post by aco on 2006-12-10
ok there is no output i write fdis -l in terminal and nothing 

aleksandar@aleksandar-desktop:~$ fdisk -l
aleksandar@aleksandar-desktop:~$

---

### Post by Azakus on 2006-12-10
Do "sudo fdisk -l"

---

### Post by aco on 2006-12-11
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12789   102727611    7  HPFS/NTFS
/dev/sda2           21714       38913   138159000    5  Extended
/dev/sda3           13427       21713    66565327+  83  Linux
/dev/sda4           12790       13426     5116702+  82  Linux swap / Solaris
/dev/sda5           21714       38913   138158968+  83  Linux

Partition table entries are not in disk order




here it is

---

### Post by aco on 2006-12-11
ppl help please anyone..i need those udf dvd's

---

### Post by riven0 on 2006-12-11
Oops! Sorry, aco, I don't know what I was thinking; the fdisk won't show your dvd drive. Can you post the output of your /etc/fstab here?


BTW, when you go to your media folder, do you see a cd or dvd-rom drive there?

---

### Post by aco on 2006-12-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=53e5c37b-cd6e-48a3-8071-5a7d4f6d2b9a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=836c735c-2daa-4b05-b83c-d039bd0a8cbb /backup         ext3    defaults        0       2
# /dev/sda1
UUID=4A3CD10B3CD0F2C5 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=b829cd85-9013-429b-88d5-b7c09f998cfc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0





and yes i can see dvd recorder and dvd player

---

### Post by aco on 2006-12-12
Ok what to do now?

---

### Post by Laryllan on 2006-12-12
I cannot read UDF DVDs too. :-k

---

### Post by aco on 2006-12-12
It seems noone can and noone knows the answer why or how? :(

---

### Post by Laryllan on 2006-12-12
In my case, the system recognizes the disc and it's name, but proposes to mount it. If I try to mount it, is states that this is not possible. In other words - deadloop.
After several hundred tries I finally gave up. :p 

All CDs have been burned with PlexTools (a Plextor only program) and IIRC the filesystem used is UDF only, i.e. *not* ISO/UDF or something like that.

---

### Post by aco on 2006-12-12
Well i can open it, it got its name everything ok, but instead of files and folders i get only one .txt file

---

### Post by Laryllan on 2007-01-12
Still no news on this issue?

---

### Post by 53ph on 2007-01-14
I mount udf DVDs regulary, with 
```
sudo mount -t udf /dev/hdc /media/cdrom0
```
Where /dev/hdc is my CD-ROM drive and /media/cdrom0 my ubuntu standard mountpoint for it. 
I believe udf support is built into the kernel - so udftools are _not needed_ (I don't have them).
If you mount through the commandline, it's better to unmount again with it,
GNOME's Eject command makes problems with that.

---

### Post by Giltine238 on 2007-01-21
I guess the above works for all of us. But I am getting really annoyed manually mounting my UDF DVDs every time, there has got to be a way for Ubuntu to mount them automatically

---

### Post by satanius on 2007-02-07
I had the same problem. When manually mounting udf disk, it says that can mount only in read only mode. So i thought i could try adding read only option into fstab, and it worked! My fstab dvdrom line now looks like this:

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto     0       0

and it all works ok, it mounts udf and iso9600 disks automatically when inserted, and burning also works (i tried only cd burning, haven't got any rw dvds at the moment). I hope this helps.

---

