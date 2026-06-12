---
title: "Advise on this fileserver and backup solution please ..."
date: 2008-02-02
forum: General Help
---

### Post by zartoop on 2008-02-02
Hi there,

Recently had a major disaster and backups failed.

Current system is mac and pc with p2p ethernet.

Choices were to buy 2Tb of external drives (bad value as storage requirements are growing at 1Tb per qtr) - decided to build own box based on intel, linux  to act as fileserver and network backup and archive.

new box
case that can hold up to 22 drives
motherboard gigabyte GA-P35-DS3P
processor intel core 2 duo 2.66GHz
2gb ram
video gigabyte gv-rx24p256h
6 500Gb SATAII hotswap storage drives - 3Tb
1 OS drive 80Gb IDE

this will be connected into network via gigabit ethernet

box will only be used for file serving, backup and archive

- is this a sensible setup?
- which linux distro would best serve my needs - choices so far are ubuntu, kubuntu, centos, fedora core (a gui for all admin is important as I am very much a command line/linux newbie)
- bacula

Any help or advice very much appreciated.

BTW - in case you are interested the whole setup is costing $2000 aud for 3Tb which in my book is great value compared to just external enclosures.

---

### Post by rogblake on 2008-02-02
The problem I see here is no fault tolerance --  you don't say exactly how you'll be using the 6 500GB drives, but if you're going to stripe across them with no parity to get a 3TB yield, you'll lose it all if a single drive craters. Also a single OS drive.

Not too long ago I put together a similar but somewhat lower capacity server. Using an 8-port 3Ware RAID controller, the server has a pair of mirrored 160GB drives for the OS plus 6 500GB drives arranged in a RAID6 array for data. This yields 2TB of data storage that can survive simultaneous failure of 2 drives, and of course if one of the OS drives fails the server will still run.

The operating system was Ubuntu Linux 7.04, desktop edition since the people administering it need the GUI. Gigabit networking with jumbo frames (9014 bytes) is used, and performance is excellent. (I forget the exact model of motherboard but it was an Intel with built-in Intel gigabit NICs. Intel network hardware is well-supported in Linux.) 

For backup we use an external ESATA drive cage with 2 750GB drives in a software RAID0 array for full backups (this will do until more than 1.5TB is used), plus a removable 750GB hot-swap drive for differential backups. Tar is used for backups since I've used it for ages and it's universal on Unix-type systems, but there are a lot of choices to be had as far as backup software.

---

### Post by nemilar on 2008-02-02
Instead of Linux, you may consider[FreeNAS]("http://www.freenas.org/").

---

### Post by zartoop on 2008-02-03
rogblake
Thanks for the advice. Yes the arrangement of the drives initially will be somewhat problematical until I buy more drives.

Your idea of mirrored OS drives is good and I will do that.

2 x 500 RAID 1 for OS

1 x 500 for file serving (expand as necessary as JBOD)

2 x 500 RAID 1 for archive (expand as necessary as raid 1 then raid 5)

4 x 500 JBOD for backup (expand first as money allows to raid 5)

backups will consist of first three items

I figure in the first instance that JBOD is OK as backup and file serving as it is unlikely that the primary data and the backup will fail concurrently (hope Murphy isn't listening)

Will be using software raid only as it is not device dependant - basically if anything goes wrong with the hardware the drives can be mounted on any system and the data retrieved.

---

### Post by zartoop on 2008-02-03
nemilar - thanks i'll check it out


WOW - first look says that this is great - seems like even an idiot like me could use this

---

### Post by zartoop on 2008-02-03
FreeNAS

I think is is really going to make my life very easy - my only concern is stability - the first stable release was at Xmas and there are few worrying issues in their forums.

Do you or others have any experience with FreeNAS to put my mind at ease.

Apart from that it does everything

- network file shares
- network back up via RSYNC
- RAID
- volume management

Have missed something obvious?

---

