---
title: "mounting software NTFS raid array"
date: 2006-11-03
forum: General Help
---

### Post by dusk on 2006-11-03
I am trying to make the switch from WinXP -> linux, but have ran into some troubles along the way.

My setup includes an ASUS a7n8x-D mobo equipped with 2 seagate 250gig SATA drives in software (mobo) raid 1.   I am running edgy.  

fdisk -l shows the two drives as: 

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


```

My question (since all my music, movies, and assorted files are important), is how can I mount this file system so I may read/write it in linux?

Thanks for any and all help.

---

### Post by dusk on 2006-11-03
Ok, so I did a little more reading and tinkering, and was able to mount the device (I think), but was unable to access it (permission denied as non-root, "invalid command: cd" as root).  

I'll walk you through it:

Show what dmraid found:
```

diablo% sudo dmraid -l
hpt37x : Highpoint HPT37X (S,0,1,10,01)
hpt45x : Highpoint HPT45X (S,0,1,10)
isw    : Intel Software RAID (0,1)
lsi    : LSI Logic MegaRAID (0,1,10)
nvidia : NVidia RAID (S,0,1,10)
pdc    : Promise FastTrack (S,0,1,10)
sil    : Silicon Image(tm) Medley(tm) (0,1,10)
via    : VIA Software RAID (S,0,1,10)
dos    : DOS partitions on SW RAIDs

```

Now reset it:
```

diablo% sudo dmraid -an

```

Activate your device (in my case sil):
```

diablo% sudo dmraid -ay -f sil

```

Is it there?
```

diablo% ls /dev/mapper        
control  sil_agadafagbgdh  sil_agadafagbgdh1

```

The first one, I'm guessing, is the entire array, while the second (ending in 1) is the partition.

Mount the PARTITION:
```
diablo% sudo mount -o ro -t ntfs /dev/mapper/sil_agadafagbgdh1 /mnt/windows

```

It should work, right?

So why do I get this: 

```

diablo% cd /mnt/windows
cd: permission denied: /mnt/windows
diablo% sudo -i cd /mnt/windows
-bash: cd: No such file or directory

```

:(

---

### Post by givré on 2006-11-03
if you want ntfs with read/write support, you can use ntfs-3g :
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
[www.ntfs-3g.org](www.ntfs-3g.org)

---

### Post by dusk on 2006-11-06
that worked perfectly, thanks

---

