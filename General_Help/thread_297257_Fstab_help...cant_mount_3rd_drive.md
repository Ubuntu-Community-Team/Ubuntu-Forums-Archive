---
title: "Fstab help...cant mount 3rd drive"
date: 2006-11-10
forum: General Help
---

### Post by jkvv_1973 on 2006-11-10
I need help to mount sdb1 (250gb drive)

Im currently using diskmounter with success on my other drives...Ive been able to mount sdb1 succesfully via this command

> sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o nls=utf8,umask=0222

but since I got diskmounter I havent been able to mount it anymore...diskmounter left this drive out...

pls help me edit my fstab ...thanks in advance:confused: 



Here are my disks...


> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14377   115483221    7  HPFS/NTFS
/dev/sda2   *       14378       19269    39294990   83  Linux
/dev/sda3           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706   42  SFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19451   156240126    c  W95 FAT32 (LBA)


MY FSTAB-----

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/hda1 /media/hda1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Manually added by jkvv
/dev/sdb1 /media/sdb1 ntfs
noauto,users 0 0

---

### Post by taurus on 2006-11-10
Try making the last line in /etc/fstab to look like this!

```

/dev/sdb1  /media/sdb1  ntfs  defaults,umask=0222  0  0

```

---

### Post by jkvv_1973 on 2006-11-10
I get error msg

> You do not have the permissions necessary to view the contents of "sdb1".


why is this? did what you said with other combos (after nfts) and still doesnt work

---

### Post by jkvv_1973 on 2006-11-10
CORRECTION

did a reboot and now I can see the files and use the files....+the icon on my desktop

thanks alot TAURUS (my sign in real life)

pls put SOLVED on my "Title"



this wasnt on the guide + Im a noob
> 
/dev/sdb1  /media/sdb1  ntfs  defaults,umask=0222  0  0

---

