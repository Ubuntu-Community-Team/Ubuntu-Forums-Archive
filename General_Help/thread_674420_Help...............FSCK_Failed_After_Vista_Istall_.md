---
title: "Help...............FSCK Failed After Vista Istall and grub recovery:("
date: 2008-01-21
forum: General Help
---

### Post by ubuntelite on 2008-01-21
[SIZE="3"]hello
i had a dual boot xp/fiesty working very well. i added a vista partition and lo and behold the vista bootloader took over so i went and stup grub usng the live cd so that ubuntu would manage all boot sequences. now i only can boot into xp, and, ubuntu only with the error that the file system check fsck failed on one of the linux partitions. the log from var/log/fsck/checkfs is given below:
************************************************** ************************************************** *****************
Log of fsck -C -R -A -a
Mon Jan 21 13:50:13 2008

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda7: 37 files, 38/1918827 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda8: 37 files, 38/1919329 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb6: 19123 files, 1715837/1918827 clusters
/dev/sda9: clean, 1035/3204992 files, 206663/6399886 blocks
/dev/sdb7: clean, 11/3204992 files, 144631/6399886 blocks
fsck.ext3: Unable to resolve 'UUID=37432f80-235c-4c46-bd97-1af5da02429c'

fsck died with exit status 8

Mon Jan 21 13:50:29 2008
----------------
************************************************** ************************************************** **********************

i have 7.04 and dont know why the vista loader got lost i thought it wouuld supersede that of xp. anyhow now i can't boot into vista at all and ubuntu only after pressing ctrl+delete to bypass the error messages on check disks. i do't know what may have gone wrong. before i set up grub, i was getting vista and xp as a secondary choice. previous to that i used to had xp and ubuntu feisty under grub. since vista messed up grub, i fixed grub using:

use the live cd
sudo grub
find /boot/grub/stage1
returns hd (0,2)
then:
root hd (0,2)
and finally
setup hd(0)
i have done this many times in the past and never ha a problem. can anyone tell me why i am getting the file error on ubuntu and missing vista in the boot sequence?

thank you all.

regards.

an ubuntulite.

keep smiling evenwhen you don't feel like it.[/SIZE]

---

### Post by plucky on 2008-01-22
ubuntelite,

Can't help with the Vista boot problem but can with the fsck problem

> fsck.ext3: Unable to resolve 'UUID=37432f80-235c-4c46-bd97-1af5da02429c'

This is caused by the **UUID** in **/etc/fstab** being different to the uuid it has currently on disk.
If you boot all the way into Ubuntu and open a terminal and input ```
cat /etc/fstab
``` you will see as an example > # /dev/hdax
UUID=37432f80-235c-4c46-bd97-1af5da02429c /home           ext3    defaults        0       2


with a line that has a UUID=37432f80-235c-4c46-bd97-1af5da02429c the UUID it couldn't resolve.

To find out the correct UUID for that line open a terminal and type ```
blkid
``` and this will output all of the current UUID's on the disk.
Just copy and replace the correct UUID into Fstab by ```
gksudo gedit /etc/fstab
```

Hope this helps.

---

