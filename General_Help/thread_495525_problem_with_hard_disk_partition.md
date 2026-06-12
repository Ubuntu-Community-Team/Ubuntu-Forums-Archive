---
title: "problem with hard disk partition"
date: 2007-07-08
forum: General Help
---

### Post by armeria on 2007-07-08
I install Windows XP and Ubuntu 7.04 dual system in my  computer. 

When I use fdisk check the partition of my hard disk, I get the message as following:

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2589 20789968+ 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 2590 9729 57352050 f W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3 2590 2590 1386 bb Boot Wizard hidden
Partition 3 does not end on cylinder boundary.
/dev/sda5 2590 4502 15361888+ b W95 FAT32
/dev/sda6 4503 5354 6838933+ b W95 FAT32
/dev/sda7 5354 5596 1951866 82 Linux swap / Solaris
/dev/sda8 5597 8028 19535008+ 83 Linux
/dev/sda9 8029 9729 13663251 83 Linux 

And gparted can't recognize the partition.

But I can run the windows and linux system without any problem. 

I want to get rid off the annoying message of the partition.

Could anyone help me? Thanks!

---

### Post by armeria on 2007-07-08
Could anyone help me? 

Thanks!

---

### Post by armeria on 2007-07-09
Could anyone help me?

Thanks!

---

### Post by bigken on 2007-07-09
try searching these **[google]("http://www.google.co.uk/search?q=Partition+3+does+not+end+on+cylinder+boundary.&ie=utf-8&oe=utf-8&aq=t&rls=Swiftfox:en-US:unofficial&client=firefox-a")** results

---

### Post by armeria on 2007-07-09
thanks! I will try.

---

