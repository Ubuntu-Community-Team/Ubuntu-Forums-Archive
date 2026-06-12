---
title: "Mount Problem"
date: 2007-03-16
forum: General Help
---

### Post by nerds in parties on 2007-03-16
hi there. I have an external hard drive tha when i try to access it from my ubuntu 6.10 i get this error:

"unable to mount the selected volume"

what can I do?

ps: in that external I keep my most important files. the last thing i want is these files to be deleted...

thanks

---

### Post by chewearn on 2007-03-16
> **nerds in parties said:**
> hi there. I have an external hard drive
What type of external harddisk; is it USB, ethernet, firewire,... ?

>  tha when i try to access it from my ubuntu 6.10 i get this error:
"unable to mount the selected volume"

What command did you run when get this error message?

---

### Post by nerds in parties on 2007-03-16
> **AstalaVista said:**
> What type of external harddisk; is it USB, ethernet, firewire,... ?



What command did you run when get this error message?

its USB, ntfs.

maybe can you tell me the commant for the module for the ntfs? maybe i dont have it already...

---

### Post by nerds in parties on 2007-03-16
no no commant. i just went to Places->Computer. its there but without access.

---

### Post by chewearn on 2007-03-16
Please post output from the following, thanks:
```
cat /etc/fstab
``````
sudo fdisk -l
```

---

### Post by Dailydog on 2008-03-28
Hi

I have the same problem. I've tried the commands you suggested and this is the output.


root@haruki:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a33157e3-c534-4d15-bb12-8b0701465c89 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=07d3da06-dd11-481f-8a37-2061d602a8ec none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
root@haruki:~# sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x429aee8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       


I've just switched to a new laptop and a brand new ubuntu install. I have a backup of my desktop on a usb external hard drive, but I cannot mount it. My husband runs the latest ubuntu too and had no problem accessing the drive.

t

---

