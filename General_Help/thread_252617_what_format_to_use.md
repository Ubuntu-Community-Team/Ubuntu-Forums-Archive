---
title: "what format to use?"
date: 2006-09-07
forum: General Help
---

### Post by jensenhearing on 2006-09-07
Installed Ubuntu on partition 3 and all was well. Then I decided to format partition 5 with "extended 2" format (didn't know what it was all about anyway) but now it says partition 5 (which was FAT32 format formerly) is not inaccessible even when I try to enable it. Then tried to format using "extended3" but it won't change from "extended 2". What's the correct method to formating? After formating it still says FREE SPACE NOT AVAILABLE.

---

### Post by croak77 on 2006-09-07
How many primary partitions do you have? You can only have 4. So if you are trying to create a 5th primary partition, it won't work

---

### Post by jensenhearing on 2006-09-07
Had 3 partitions on Windows98 FAT32 format. The ubuntu install disk detected annother 4 GB of FREE space to install. and another 270 MB of space for swap partition.

So it says in system > disk > partition that there's 7

All I did was to format partition 5 to ext2 instead of ext3 and now my itchy fingers when to change it to swap parition and cannot be formated back to ext2 or ext3

---

