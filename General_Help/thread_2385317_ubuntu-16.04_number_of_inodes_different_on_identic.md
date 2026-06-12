---
title: "ubuntu-16.04 number of inodes different on identical external usb3 hds"
date: 2018-02-19
forum: General Help
---

### Post by dieter-erich on 2018-02-19
Hi all,
   working with many files I recently run out of inodes: "EXT4-fs warning (device sdb1): ext4_dx_add_entry:2217: inode #232194049: comm python: Directory index full!"
I was thus wondering whether the number of inodes was related to the size of the HD, but it seems completely erratic:

despite all these external TOSHIBA HDs having the same size (6 TB) they have very different numbers of inodes:

"df -i|grep -E 'Filesystem|TOSH"

gives:

Filesystem        Inodes   IUsed     IFree IUse% Mounted on
/dev/sdg2       15570988  109696  15461292    1% /media/xxx/TOSHIBA3
/dev/sde2       28118368 5768693  22349675   21% /media/xxx/TOSHIBA6
/dev/sdf2      557458772  273030 557185742    1% /media/xxx/TOSHIBA5
/dev/sdh2      521670556  121363 521549193    1% /media/xxx/TOSHIBA7

So, the number of total 'Inodes' is completely different from each other despite of the disks being identical. I just mounted them as NTFS file system on arrival from the dealer.

 My questions: how comes that individual but identical disks have so different numbers of inodes? And: How can I increase the number of inodes on a given disk (in particular on an ext4-formatted internal one that has 12 TB)?
Thanks, DE

---

### Post by wildmanne39 on 2018-02-19
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by TheFu on 2018-02-19
Inodes are set at file system creation time.  These are reserved areas on the disk, so ... that reservation happens when the file system is created.  **It cannot be altered later.**
[https://unix.stackexchange.com/questions/26598/how-can-i-increase-the-number-of-inodes-in-an-ext4-filesystem](https://unix.stackexchange.com/questions/26598/how-can-i-increase-the-number-of-inodes-in-an-ext4-filesystem)

Wikipedia has a nice article about inodes too.

Basically, there are a few ways to solve the issue.
* backup all the data to different storage, manually recreate the file system on the old storage, specifying 10x-100x more inodes, restore the data back to the original storage.
* Split the files (probably at a top-level directory) between different partitions.  If you have fewer large files, then the default for inodes is probably fine. If you have billions of tiny files, you'll want to make more than the default number of inodes when you create the new file system on the partition(s).

BTW, you aren't the first with this issue. I have a server that has a few web apps. These are full of tiny perl and python and ruby files.  Ended up adding more storage under /var/www/ with 100x the default number of inodes.  Because the issue was millions of tiny files, I didn't need to add much real storage to make a difference.  Actually only added 2G more.

For non-OS file systems, you might want to quickly make the 5% reserved-for-root space available. This could free up some inodes that are otherwise locked up.  tune2fs is the command.  On a 12T disk, 5% is a bunch - 600G by my calcs.  On the partition with the OS, please don't remove the reserved space below 1-2G. Bad things can happen.  If there is a bunch of churn in the file system, fragmentation can happen if you don't leave the disk with sufficient work space for stuff too.

---

### Post by dieter-erich on 2018-02-19
Hi TheFu,
  thanks for this explanation and the link! They were most useful! I only do not understand why identical disks that were identically formatted show a different number of total inodes!
D-E

---

### Post by TheFu on 2018-02-19
I don't know anything about NTFS.  I thought we were talking about ext4.  My mistake.

BTW, I didn't look at the numbers - too hard to read without "code tags" so things line up.
I see now that sdb wasn't included in the output.

---

### Post by dieter-erich on 2018-02-20
OK, anyhow, thank you very much

---

