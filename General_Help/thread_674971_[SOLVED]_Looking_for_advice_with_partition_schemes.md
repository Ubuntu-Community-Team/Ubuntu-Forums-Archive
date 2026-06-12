---
title: "[SOLVED] Looking for advice with partition schemes"
date: 2008-01-22
forum: General Help
---

### Post by aephex on 2008-01-22
I'm looking for help and advice with creating a partition scheme for a multiple-boot system.

Specs:
AMD 3700+ 64Bit (will be running 32bit)
1GB RAM
300GB HDD
External 250GB SSD (Not to be included in scheme, but could be used for inter-OS files, currently my media storage and backup drive.)

Minimum 3 operating systems. 
Ubuntu 7.10:
for daily use, web design/development, multimedia, and office tasks.

WinXP:
for web design/development, and gaming.

Constantly changing Linux distro:
for evaluation.

I understand that I should have at least: boot, swap, and 1 partition for each OS.
Should I create a "data" or "storage" partition, and if so, what filesystem?
Are there any other partitions I should create? ( Filesharing between OSes )
Are there any invaluable programs or tools that I shouldn't go without?
What are the recommended sizes and types for the partitions?

If you want to be really helpful you can go so far as to lay out your suggested scheme, 
(Device,  Boot,  Size,  Id,  System, Description)

Any helpful information is welcome. Thanks.

---

### Post by jclmusic on 2008-01-22
seems to me like u got it pretty much sorted. just remember that windoze can't read ext2/3 or some other linux partitions, and linux's support for ntfs is still in development, so it's best to have shared files on a fat32 partition.

i would reccomend:
1 partition for ubuntu (ext3)
1 partition for windoze (ntfs or fat32)
1 partition for testing linux distros (ext3 or xfs)
1 partition for all your data (fat32)
1 partition for swap

---

### Post by aephex on 2008-01-22
> **jclmusic said:**
> seems to me like u got it pretty much sorted. just remember that windoze can't read ext2/3 or some other linux partitions, and linux's support for ntfs is still in development, so it's best to have shared files on a fat32 partition.

i would reccomend:
1 partition for ubuntu (ext3)
1 partition for windoze (ntfs or fat32)
1 partition for testing linux distros (ext3 or xfs)
1 partition for all your data (fat32)
1 partition for swap

Your scheme didn't include a separate boot partition, if I don't make a separate boot partition does it matter about which partitions are primary? I think I remember hearing something about Windows not liking to be anywhere but a primary partition. Can't be sure tho. Is it even advisable to make a small, yet separate, boot partition?

Anyone else that has advice or experience, please add your thoughts.

---

### Post by aephex on 2008-01-23
I've decided on a scheme and implemented it.
I thought I would share with everyone what I did.

300GB HDD:
*Primary - NTFS - 40GB - WinXP
*Primary - ext3  - 40GB - Ubuntu
*Unallocated -   - 20GB - To be used for undecided distro.
*Extended -       - 200GB:
 -- Logical - FAT32 - 197GB - Shared Data
 -- Logical - Linux-Swap - 3GB - Swap to be used by all linux distros

It turned out the part I really didn't understand were the constraints and capabilities of the different types of partitions (primary, logical, extended). A few headbutts later and I decided to just go ahead and this is what I came out with. So far, it works quite well.

Most people can probably use a smaller swap file, I erred on the safe size as I will be doing a lot of intensive rendering and compiling.

---

### Post by jclmusic on 2008-01-23
a seperate boot partition would only be needed if your motherboard was too old to read past a certain number of sectors.

---

