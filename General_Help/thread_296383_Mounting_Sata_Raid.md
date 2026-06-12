---
title: "Mounting Sata Raid"
date: 2006-11-09
forum: General Help
---

### Post by [sYn] on 2006-11-09
Hello All!

I just installed edgy on my main machine, setup most of the needed applications and got beryl working nicely.. Now all I need is to get my Sata Raid mounted so I can access my main information drive..

Using a Intel 82801ER (ICH5R) SATA Controller on an Intel 865 Motherboard.. 2 MAXTOR SATA drives as can be seen below..

The problem
```
syn@DECODED-LINUX:/media$ sudo mount -t ntfs /dev/sda1 /media/Dump
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

fdisk -l information..

```
syn@DECODED-LINUX:/media$ sudo fdisk -l

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11603    93201066    7  HPFS/NTFS
/dev/hda2           11604       14946    26852647+   f  W95 Ext'd (LBA)
/dev/hda5           14686       14946     2096451   82  Linux swap / Solaris
/dev/hda6           11604       14685    24756102   83  Linux

Partition table entries are not in disk order

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       30400   244187968+   7  HPFS/NTFS

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/hdd5               2       30401   244187968+   7  HPFS/NTFS

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       72967   586107396    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table
```

df -h and and fstab contents
```
syn@DECODED-LINUX:/media$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda6              24G  2.2G   22G  10% /
varrun               1013M  132K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
procbususb             10M  176K  9.9M   2% /proc/bus/usb
udev                   10M  176K  9.9M   2% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   18M  995M   2% /lib/modules/2.6.17-10-386/volatile
/dev/hdd5             233G  213G   21G  92% /media/Dump2
/dev/hdc1             233G   66G  168G  28% /media/Dump3
/dev/hda1              89G   63G   27G  70% /media/Windows
syn@DECODED-LINUX:/media$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=58085baf-cfc6-40e6-b146-685d0d4f4c06 /               reiserfs notail          0       1
# /dev/hdd5
UUID=F88C6A6C8C6A24FA /media/Dump2    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=64380F48380F1926 /media/Dump3    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=CE1C493E1C4922B7 /media/Windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=31e6ae55-3f11-4ad5-90b9-e8527638d2d2 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

Any pointers would be great, do you think following the tutorial at the link below would solve the problem?

[http://www.ubuntuforums.org/showthread.php?t=2557](http://www.ubuntuforums.org/showthread.php?t=2557)

---

### Post by sjashton on 2006-11-09
I followed that how to a couple of weeks back and instantly got read access to my SATA RAID (VIA 8257), read through the thread though, ithink i remember a reply in there relating to a typo in the original post. Also, i had to install DMRAID in synaptic to get it working. I'm running Dapper

---

