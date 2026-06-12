---
title: "3TB NTFS Partitioning"
date: 2012-10-29
forum: General Help
---

### Post by synthecypher on 2012-10-29
I'm trying to setup an Amahi server which uses ubuntu I've got two 3TB Seagate Barracudas (ST3000DM001) and when I try to format them using Disk Utility as NTFS I get the following warning:

"WARNING: The partition is misaligned by 3072 bytes. This may result in very poor performance. Repartitioning is suggested."

How do I fix this? (I'm a complete n00b to ubuntu)

Thanks in advance, :)

---

### Post by oldfred on 2012-10-29
I have never used Disk Utility for partitioning. 

If you use gparted it automatically align, but I am not sure when it sees your drive if it will default to gpt or not. You need gpt partitioning.

Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

If you want a command line tool for gpt you can download gdisk. You should download it anyway in your install as fdisk does not work gpt drives.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

Do you have Windows installed? You should because you will need to run chkdsk periodically on NTFS partitions and if 3TB it may take a while. Ubuntu automatically runs fsck or can be set to run on Linux formated partitions after so many reboots.

---

### Post by synthecypher on 2012-10-29
You'll have to dial it back a bit for me.

I downloaded GParted Partition Editor from the Ubuntu Software Centre and that seemed to format them as NTFS with no warnings once viewed in Disk Utility.

What's the business about running chkdisk from Windows? Why do I need to do this?

---

### Post by oldfred on 2012-10-29
Same reason you run e2fsck or fsck in Linux. Files start to get corrupted, drives develop issues. Ordinary maintenance.

My old XP install booted but then one day gparted would not show the entire drive XP was on. Only after running chkdsk did gparted show my drive, and XP booted a bit faster.

If you are only running Linux you should not use NTFS.

---

