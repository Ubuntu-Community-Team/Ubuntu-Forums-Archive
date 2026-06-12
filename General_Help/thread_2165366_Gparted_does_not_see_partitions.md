---
title: "Gparted does not see partitions"
date: 2013-08-04
forum: General Help
---

### Post by hans12345 on 2013-08-04
I have the opposite problem, which someday I shall try and fix.

I have a 500 GB disk, with 2 partitions, 120 GB and 380 GB, plus a tiny one at the end with a few left over MB.

It works fine. I have files on sda1 and sda2.

But Gparted will not touch it. I tried several utilities on it. They seem to think I have a 1 TB disk. 

Clonezilla spent a long time backing up the tiny 3rd partition, which it said was an unknown format.

fdisk -l shows sda2 and sda3 as being unknown format

I tried once to install Linux on the 2nd partition, but of course it failed.

But since the disk works I never got around to finding out what is wrong.

Comments anyone?

Hans

---

### Post by oldfred on 2013-08-04
Moved to your own thread as issue is different & on page 4 of that thread it would get lost. Was here:
[http://ubuntuforums.org/showthread.php?t=2164446](http://ubuntuforums.org/showthread.php?t=2164446)

Post this:
 sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print

Sometimes issues from gparted include, chkdsk or hibernation on NTFS partitions, dynamic partitions from using Windows to create partitions, left over gpt partition info on MBR(msdos) partitioned drive so gparted does not know if gpt or MBR, left over RAID meta-data on a drive that was previously RAID, maybe some others.

---

