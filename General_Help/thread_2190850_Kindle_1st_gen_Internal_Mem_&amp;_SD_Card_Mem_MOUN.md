---
title: "Kindle 1st gen Internal Mem &amp; SD Card Mem MOUNTING"
date: 2013-11-29
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-11-29
My 1st generation Kindle, has both an internal memory and an sd card slot memory.

Disk /dev/sdb: 192 MB, 192202752 bytes
6 heads, 62 sectors/track, 1009 cylinders, total 375396 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1017 MB, 1017643008 bytes
32 heads, 61 sectors/track, 1018 cylinders, total 1987584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ac97e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              61     1987135      993537+   c  W95 FAT32 (LBA)

I want to make the Kindle's memory(s) part of fstab. I'm doing this because the Kindle is having odd mount time problems with Calibre. Sometimes Calibre finds the memory and sometimes not. Sometimes unplugging and plugging the Kindle into the 'puter helps Calibre find the memory and sometimes not. Sometimes, both memories mount, sometimes, only the Kindle "internal" memory.

I want to add the Kindle's memory into fstab and know to make directory(s) in /media, e.g., /media/kindle - but I'm confused as to how to go about dealing with the 2 memories the Kindle tells Ubuntu it has.

---

