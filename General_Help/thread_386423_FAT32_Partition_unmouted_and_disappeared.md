---
title: "FAT32 Partition unmouted and disappeared"
date: 2007-03-17
forum: General Help
---

### Post by Jcarr_toonist on 2007-03-17
I have a computer with a dual boot winxp/edgy with windows running on my SATA drive and ubuntu running on my IDE. On the SATA I have a fat32 partition which I mounted automatically in ubuntu so that I can listen to my music in both windows and ubuntu. 

Oddly the other day while I was listening to my music, the partition was no longer mounted and ubuntu will no longer detect my SATA drive. This all happened mid-song and I am still a little too new to ubuntu to know what to do.

here is the entry in my fstab...
> # /dev/sda5 -- converted during upgrade to edgy
UUID=45A3-8805 /home/music vfat defaults,utf8,umask=007,gid=46 0 1

I have tried manually mounting the sata and it claims that the device doesn't exist. As well I poked around in GNOME partition editor and it too has never heard of my sata drive. Windows still detects the fat32 partition just fine. 

Thanks in advance.

---

### Post by taurus on 2007-03-17
What's the output of this command from a terminal?

```
sudo fdisk -l
```
And might as well post your /etc/fstab here too.

```
cat /etc/fstab
```

---

### Post by Jcarr_toonist on 2007-03-17
> Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9128    73320628+  83  Linux
/dev/hda2            9203       13819    37086052+  83  Linux
/dev/hda3           13820       14469     5221125   82  Linux swap / Solaris
/dev/hda4           14470       14596     1020127+   b  W95 FAT32

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=9f775acb-43b6-4eec-a5f9-814157a3b637 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=ac2ff3c7-72e8-4d59-9624-dd1eca6997b7 /home/movies ext3 defaults,user 0 2
# /dev/sda5 -- converted during upgrade to edgy
UUID=45A3-8805 /home/music vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda3 -- converted during upgrade to edgy
# UUID=6706ce1f-5a55-44d8-a393-4348a9b8eb30 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/dvdrecorder      udf,iso9660     user,noauto,rw  0      0

t

---

### Post by taurus on 2007-03-17
Well, I don't see any SATA or external harddrive on your machine, /dev/sda.  Do you have a SATA harddrive on your machine or are you talking about /dev/hda4?

---

### Post by Jcarr_toonist on 2007-03-17
No I definitely have a sata on my computer, it has my windows installation at that very least. hda4 is just a makeshift partition I made until I can get my main one working again.

---

### Post by taurus on 2007-03-17
And you can boot your Windows on that SATA drive?

---

### Post by Jcarr_toonist on 2007-03-17
Yeah just fine and my music fat32 partition show up there as well, completely intact.

---

