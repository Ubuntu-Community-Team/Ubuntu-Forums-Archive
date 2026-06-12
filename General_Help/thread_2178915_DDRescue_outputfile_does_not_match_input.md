---
title: "DDRescue outputfile does not match input"
date: 2013-10-05
forum: General Help
---

### Post by the_jlx on 2013-10-05
trying to rescue a NTFS partition but this is not at all what i expected.

commandline
```
ddrescue -v -p -b 512 -r 1 -c 128 -T 600 /dev/sde1 /media/jlx/D83ACAA83ACA834C/w7lol/fudge.iso /home/jlx/Desktop/erh
```
 
output result
```
fdisk -l fudge.iso
 
Disk fudge.iso: 160.0 GB, 160039240704 bytes
255 heads, 63 sectors/track, 19456 cylinders, total 312576642 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373
 
This doesn't look like a partition table
Probably you selected the wrong device.
 
    Device Boot      Start         End      Blocks   Id  System
fudge.iso1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
fudge.iso2   ?  1917848077  2462285169   272218546+  73  Unknown
fudge.iso3   ?  1818575915  2362751050   272087568   2b  Unknown
fudge.iso4   ?  2844524554  2844579527       27487   61  SpeedStor
 
Partition table entries are not in disk order
```

---

