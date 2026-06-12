---
title: "GParted/fdisk not listing all partitions on drive, something's wrong..."
date: 2008-01-12
forum: General Help
---

### Post by 3ntity on 2008-01-12
I don't know what happened, but suddenly the partitions on a secondary HDD aren't listed properly under GParted (see attached screenshot) nor fdisk anymore.
```
$ fdisk -l /dev/sda
Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1664    12579808+   7  HPFS/NTFS
/dev/sda2            3329       25841   170198280    f  W95 Ext'd (LBA)
/dev/sda5            3329       25841   170198248+   7  HPFS/NTFS
```
after /dev/sda1 there's supposed to be another 2 partitions: one ext 3 (w/ Ubuntu on it), one swap.
Now using testdisk:
```
$ sudo testdisk /dev/sda
-> Proceed using Disk /dev/sda - 200GB / 186 GiB
-> Intel/PC  partition
-> Analyse
```
gives:
```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1  1566  29 63   25159617
 2 E extended LBA          3132  60  1 24320 239 63  340396560
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 5 L HPFS - NTFS           3132  61  1 24320 239 63  340396497 [Data]
```
Hitting 'Proceed' here gives me the following warning:
```
Warning: the current number of heads per cylinder is 255
but the correct value may be 240.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.
```
I've tried using the Geometry menu to set it to 240; this hasn't helped. Hitting 'Proceed' after this shows the proper disk layout:
```
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  1566 254 63   25173792
D Linux                 1566  30  1  2871 254 63   20979000
D Linux Swap            2871 136  1  3132 254 63    4200462
D HPFS - NTFS           3132  61  1 24320 254 63  340397442 [Data]
 keys to select partition.Left/Right Arrow keys to CHANGE partition characteris
tics:Keys A: add partition, L: load backup, T: change type, P: list files, : to
 continue

Structure: Ok.  Use Up/Down Arrow keys to select partition.Left/Right Arrow ke:
Use Left/Right Arrow keys to CHANGE partition characteristics:Keys A: add partit:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=DeletedKeys A: add parti:
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 12 GB / 12 GiB
``` As you can see a 'Linux' and a 'Linux Swap' partition are listed here, but both with a 'D' before them, which are supposedly 'D=DeletedKeys'. What does this mean, and how can i fix this? 
Thanks in advance,
3phemeral

---

### Post by yozi on 2008-01-26
I have a similar problem: after running gparted, the geometry in the partition table was
changed by gparted from 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

to 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

---

### Post by dcstar on 2008-01-26
> **3ntity said:**
> 
......... As you can see a 'Linux' and a 'Linux Swap' partition are listed here, but both with a 'D' before them, which are supposedly 'D=DeletedKeys'. What does this mean, and how can i fix this? 
Thanks in advance,
3phemeral

This tool may allow you to change the partitions flags (but be VERY careful using it):

[http://www.sysresccd.org/](http://www.sysresccd.org/)

---

