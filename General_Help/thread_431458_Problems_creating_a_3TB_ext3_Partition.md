---
title: "Problems creating a 3TB ext3 Partition"
date: 2007-05-03
forum: General Help
---

### Post by BenderFHD on 2007-05-03
Since Feisty is the only Distribution which has drivers for my Promise Supertrak EX8350 Raidcontroloer onboard, I switched from Suse 10.2 to Feisty Server 64-Bit. Worked perfectly so far. The only Problem I ran into is that when I try to create a new Partition on the Systems internal Raid 5 Array (7x500GB) Feisty seams to destroy the new Partition on every Boot, so that only 750GB are left.

My procedure is the following:
Open parted and erase the old Partition
Create GPT Disc Label
mkpart primary ext3 
start: 0
end: the arraysize (Don't know the exact size right now)
After parted is finished the new partition can be mounted and the whole 3TB are accessible. But after creating an entry in /etc/fstab (/dev/sda1/  /data  ext3  defaults  0  2) and rebooting I get an fsck Error at boot time and the partition only shows 750GB.
Anybody any Ideas?

---

### Post by orb9220 on 2007-05-03
[http://www.cyberciti.biz/howto/question/static/maximum-partition-size.php](http://www.cyberciti.biz/howto/question/static/maximum-partition-size.php)

Note: * The maximum file size for ext2/ext3 is actually dependent on the choice of blocksize and hardware architecture.

[http://www.oracle.com/technology/pub/articles/calish_filesys.html](http://www.oracle.com/technology/pub/articles/calish_filesys.html)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

All thru google. Might try to google your problem first.
Wiki shows a limit of 2terabytes.

Looks like RieserFS may be the way to go.

---

