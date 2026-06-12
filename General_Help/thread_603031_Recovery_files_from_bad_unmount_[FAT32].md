---
title: "Recovery files from bad unmount [FAT32]"
date: 2007-11-04
forum: General Help
---

### Post by aweinert on 2007-11-04
I bought a 320GB ext USB HD to back up my files to before I tried to fix my failing hard disk. I copied my home directory to this disk, but it had problems unmounting [It would automatically remount in less than a second]. Unfortunately now I cannot access any of these files, and my internal hard disk is a loss. What is the best foss program/method for recovery of these files? Nothing should have been written to it after I copied the files over and had the problem.


Fdisk reports this:
$ fdisk -l

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007b76c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    b  W95 FAT32


-Thanks, 
Alex

---

