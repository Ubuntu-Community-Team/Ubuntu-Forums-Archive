---
title: "Partitioning: &quot;Partition X does not end on cylinder boundary&quot;"
date: 2006-09-18
forum: General Help
---

### Post by FRealmS on 2006-09-18
first i have 40GB HDD and my partitions are:
> /dev/hda1 * 20GB total * HPFS/NTFS * *13GB used 7GB free* * *OS:Windows XP*
/dev/hda2 * Extended
/dev/hda5 * 20GB total * HPFS/NTFS * *5GB used 15GB free*

then i resize (/dev/hda5) and make:
> ...
/dev/hda5 * 7GB total * HPFS/NTFS * *5GB used 2GB free*
/dev/hda6 * 12+GB total * ext3 * / * *OS:Ubuntu 6.06*
/dev/hda7 * ~512MB total * linux swap
everything is OK (all OS works;copy all importants files & documents to ext3) but...
> sudo fstab /dev/hda

/dev/hda1 => *7 HPFS/NTFS* --> *b W95 FAT32*
/dev/hda5 => *7* *HPFS/NTFS* --> *b W95 FAT32*
...and i mean (don't remember) */dev/hda2* in this moment are *W95 Ext'd (LBA)*
then i try to install Windows XP, but it exit with error: with *Extended LBA*  (i'm not sure)
and my stupid head make this:
> sudo fstab /dev/hda

/dev/hda1 => *b W95 FAT32* --> *c W95 FAT32 (LBA)*

then i try again to install... again error!

The result are: 
> Disk /dev/hda: 41.1 GB, 41174138880 bytes
16 heads, 63 sectors/track, 79780 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   ?     1920663     3757825   925929529+  68  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hda2   ?     1319628     1854326   269488144   79  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hda3   ?      534712     1921977   699181456   53  OnTrack DM6 Aux3
Partition 3 does not end on cylinder boundary.
/dev/hda4   ?     1383560     1383581       10668+  49  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

[ATTACH]15939[/ATTACH]
i probe to fix it with *fdisk*: 
> Expert command (m for help): f
Done.

Expert command (m for help): v
Partition 1 does not end on cylinder boundary.
Partition 1: head 78 greater than maximum 16
Partition 2 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 2.
Partition 3 does not end on cylinder boundary.
Partition 3: head 79 greater than maximum 16
Warning: partition 1 overlaps partition 3.
Warning: partition 2 overlaps partition 3.
Partition 4 does not end on cylinder boundary.
Partition 4: head 102 greater than maximum 16
Warning: partition 1 overlaps partition 4.
Total allocated sectors -1046090688 greater than the maximum 80418240

Expert command (m for help):

[ATTACH]15940[/ATTACH]
i don't write partition table. Please tell me is this output 0K???
This is with *cfdisk*: 
> FATAL ERROR: Bad primary partition 0: Partition begins after end-of-disk
Press any key to exit cfdisk

[ATTACH]15941[/ATTACH]

](*,) 

Thanks for any help

---

### Post by FRealmS on 2006-10-05
i FIX this problem with _***testdisk***_
> Package testdisk

* dapper (admin): Partition scanner and disk recovery tool [universe]
6.1-1: amd64 i386 powerpc
The problem was in *incorrect* number of ***_heads_*** **=>** *incorrect* number of ***_cylinders_***
> Disk /dev/hda: 41.1 GB, 41174138880 bytes
***_[COLOR="Red"]16 heads[/COLOR]_***, 63 sectors/track, 79780 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
*testdisk* sign, that the *correct* number must be ***_[COLOR="Red"]255 heads[/COLOR]_*** ... but *cylinders* are too much ...

the right method is to calculate it.
HEADS * SECTORS/TRACK * CYLINDERS * UNITS = BYTES

the disk /dev/hda is 40GB => number of *cylinders* must be ***_[COLOR="Red"]~5005[/COLOR]_***

after this correction, partition table is fixed and all data is OK :D

---

### Post by sdyson on 2008-01-29
Thanks for the tip. Managed to restore a damaged partition table using testdisk!

---

