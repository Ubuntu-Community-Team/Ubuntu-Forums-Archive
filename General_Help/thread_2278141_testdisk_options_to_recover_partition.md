---
title: "testdisk options to recover partition"
date: 2015-05-14
forum: General Help
---

### Post by arapaho on 2015-05-14
Testdisk analyse options shows

```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7297 255 63
     Partition               Start        End    Size in sectors
 * Linux                    0  32 33  1446 235  5   23242752
 P Linux                 1447  12 38  1459  40 53     194560
 P Linux                 1459  73 23  3283  11 56   29298688
>L Linux                 3283  44 26  7297  19 18   64483328

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large file Sparse superblock, 33 GB / 30 GiB
```

Those partitions entries are in green color.

I guess I can recover them because when I press P I can see files listed, so they seems to be ok. 

When I press enter it shows write options but

```
Disk /dev/sda - 60 GB / 55 GiB - CHS 7297 255 63

     Partition                  Start        End    Size in sectors

 1 * Linux                    0  32 33  1446 235  5   23242752
 2 P Linux                 1447  12 38  1459  40 53     194560
 3 P Linux                 1459  73 23  3283  11 56   29298688
 4 E extended LBA          3283  11 57  7297  19 18   64485376
 5 L Linux                 3283  44 26  7297  19 18   64483328
```I don't know what is
4 E extended LBA          3283  11 57  7297  19 18   64485376
so I am not sure if I should write it. 

I want to chose only two partitions to write to MBR, those numbered 3 and 5.

Ok. I pressed Enter and recovered those partitions. At the same time I lost system but it is not that important. 

Problem solved.

---

