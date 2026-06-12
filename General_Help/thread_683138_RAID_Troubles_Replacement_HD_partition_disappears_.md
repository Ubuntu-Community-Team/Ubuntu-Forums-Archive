---
title: "RAID Troubles: Replacement HD partition disappears after reboot"
date: 2008-01-30
forum: General Help
---

### Post by MackerelHead on 2008-01-30
Hello,

I set up a raid array (but don't boot off of it - its autodetected) lvl 5 formatted w/jfs. Everything was running fine, and I was sharing it w/samba.

I borrowed one of the hard drives, reinserted it, repartitioned, and used the mdadm -add cmd. It added the drive and after some time was synced and fine. After reboot, it couldn't find the replaced hard drive partition (it is no longer listed in /dev) though the drive itself is listed. Using fdisk shows the raid-autodetect partition is still there. The other disk partitions show up fine. Using fdisk to delete and recreate the partition causes it to show up again (in /dev) until the system is rebooted.

Am I missing something?

Thanks in advance.

---

### Post by MackerelHead on 2008-02-03
Solution:

The reason I borrowed the HD was to temp. use for a windows install. Using mdadm to examine /dev/hdc turned up that it was a spare - even though I had just wiped the partition table. Using that as a clue, I wiped the drive with Darik's Boot And Nuke (Sourceforge).

Afterwards, partitioning and adding the drive everything went normally, the drive synced, and reboots worked.

Cheers!

---

