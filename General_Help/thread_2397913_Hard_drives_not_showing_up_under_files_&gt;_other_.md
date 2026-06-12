---
title: "Hard drives not showing up under files &gt; other locations &gt; on this computer"
date: 2018-08-04
forum: General Help
---

### Post by killbot2 on 2018-08-04
disk utility shows both internal drives yet when I look under files >  other locations > on this computer, I only see one partition of one  of the drives, called computer. This is after doing a fresh install  where I partitioned one drive for the os, swap, and efi, and another for  /home. Another strange thing I noticed is that the drive i'm using to  boot is labeled dev/sdb, and the one for the home directory is labeled  dev/sda. I'm a total newb when it comes to linux and any help would be  greatly appreciated.

ben@SmashCan:~$ sudo fdisk -l
Disk /dev/loop0: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 4.9 MiB, 5152768 bytes, 10064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 45CB8427-5C2A-4444-84D7-A4D9E4D0B268

Device     Start       End   Sectors   Size Type
/dev/sda1   2048 625141759 625139712 298.1G Linux filesystem




Disk /dev/sdb: 57.8 GiB, 62022868992 bytes, 121138416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 208C254B-9DBA-4EE5-90CE-33640ED09A69

Device        Start      End  Sectors  Size Type
/dev/sdb1      2048 58593279 58591232   28G Linux filesystem
/dev/sdb2  58593280 89843711 31250432 14.9G Linux swap
/dev/sdb3  89843712 90820607   976896  477M EFI System


Disk /dev/loop8: 226.4 MiB, 237391872 bytes, 463656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

---

### Post by HermanAB on 2018-08-05
Linux file systems do not work like Windows file systems with multiple a:\, b:\, c:\ roots.  A Linux file system has only one 'tree' with a single 'root'.  Everything branches off that.

---

