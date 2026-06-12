---
title: "file loss with JFS formatted partition"
date: 2008-06-10
forum: General Help
---

### Post by dlenmn on 2008-06-10
First a little background:

I'm running kubuntu 8.04 with KDE 4 on a 3 disk RAID 3 array with a [netcell hardware controller]("http://www.mandriva.com/archives/en/company/press/pr/node_2174.html"). I only have one partition for the linux installation, and it is formatted as JFS. The partition dates back ~2 years. It's been giving me trouble for the last couple of months -- I'll have trouble on start up, I'll boot from an install CD, I'll run jfs_fsck, it'll find some problems (and remove some files), and then things will work for a couple of weeks before the process repeats itself. In the past, the only files I lost were configuration or temporary files I didn't care much about, but I lost some files of value the last time around (thankfully, I have a backup). Here's the output from the last time I ran jfs_fsck:

```
ubuntu@ubuntu:~$ sudo jfs_fsck -f -v /dev/sda2
jfs_fsck version 1.1.11, 05-Jun-2006
processing started: 6/7/2008 12.19.27
The current device is:  /dev/sda2
Open(...READ/WRITE EXCLUSIVE...) returned rc = 0
Primary superblock is valid.
The type of file system for the device is JFS.
Block size in bytes:  4096
Filesystem size in blocks:  50331648
**Phase 0 - Replay Journal Log
LOGREDO:  Allocating for ReDoPage:  (d) 4096 bytes
LOGREDO:  Allocating for NoDoFile:  (d) 4096 bytes
LOGREDO:  Allocating for BMap:  (d) 172248 bytes
LOGREDO:  Allocating for IMap:  (d) 28696 bytes
LOGREDO:  Log record for Sync Point at:    0x0e66e8
LOGREDO:  Beginning to update the Inode Allocation Map.
LOGREDO:  Done updating the Inode Allocation Map.
LOGREDO:  Beginning to update the Block Map.
LOGREDO:  Done updating the Block Map.
LOGREDO:  End of log found at logend = 0x0e66e8
LOGREDO:  Synch point record number:  0x0e66e8
LOGREDO:  Synch point record address:  0x0e66e8
LOGREDO:  Number of log records:    (d) 1
LOGREDO:  Number of Do blocks:    (d) 0
LOGREDO:  Number of NoDo blocks:    (d) 0
logredo returned rc = 0
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
Duplicate reference to 1 block(s) beginning at offset 47188789 found in file system object FF1251611.
Inode F1251611 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47188797 found in file system object FF1251611.
Inode F1251611 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47188811 found in file system object FF1251611.
Inode F1251611 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47188932 found in file system object FF1251611.
Inode F1251611 has references to cross linked blocks.
File system object FF1251611 has corrupt data (39).
Duplicate reference to 1 block(s) beginning at offset 47243908 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243910 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243912 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243921 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243931 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243935 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243937 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243940 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243944 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243948 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 2 block(s) beginning at offset 47243950 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243961 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243968 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243972 found in file system object FF1251627.
Duplicate reference to 2 block(s) beginning at offset 47243974 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243977 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
File system object FF1251627 has corrupt data (39).
Duplicate reference to 1 block(s) beginning at offset 47187954 found in file system object FF1308000.
Inode F1308000 has references to cross linked blocks.
File system object FF1308000 has corrupt data (39).
Duplicate reference to 1 block(s) beginning at offset 47256411 found in file system object FF1385910.
Inode F1385910 has references to cross linked blocks.
File system object FF1385910 has corrupt data (39).
Duplicate reference to 1 block(s) beginning at offset 47710250 found in file system object FF1851595.
Inode F1851595 has references to cross linked blocks.
Duplicate reference to 3 block(s) beginning at offset 47711572 found in file system object FF1851595.
Inode F1851595 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47711583 found in file system object FF1851595.
Inode F1851595 has references to cross linked blocks.
Duplicate reference to 2 block(s) beginning at offset 47711585 found in file system object FF1851595.
Inode F1851595 has references to cross linked blocks.
Duplicate reference to 2 block(s) beginning at offset 47711588 found in file system object FF1851595.
Inode F1851595 has references to cross linked blocks.
File system object FF1851595 has corrupt data (39).
Duplicate reference to 1 block(s) beginning at offset 47212052 found in file system object FF1955690.
Inode F1955690 has references to cross linked blocks.
File system object FF1955690 has corrupt data (39).
Duplicate reference to 1 block(s) beginning at offset 47188933 found in file system object DF2081716.
Inode F2081716 has references to cross linked blocks.
File system object DF2081716 has corrupt data (39).
**Phase 2 - Count links
Inode F1953810 has incorrect link count.
Incorrect link counts have been detected. Will correct.
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
Duplicate reference to 1 block(s) beginning at offset 47188789 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47188797 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47188811 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47188932 found in file system object FF1251585.
Duplicate reference to 1 block(s) beginning at offset 47188933 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47212052 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243908 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243910 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243912 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243921 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243931 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243935 found in file system object FF1251585.
Inode F1251585 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243937 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243940 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243944 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243948 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 2 block(s) beginning at offset 47243950 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243961 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243968 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243972 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 2 block(s) beginning at offset 47243974 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47243977 found in file system object FF1251596.
Inode F1251596 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47711573 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47711574 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47711583 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 2 block(s) beginning at offset 47711585 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 2 block(s) beginning at offset 47711588 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47711572 found in file system object FF1251627.
Inode F1251627 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47256411 found in file system object FF1251639.
Inode F1251639 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47187954 found in file system object FF1253212.
Inode F1253212 has references to cross linked blocks.
Duplicate reference to 1 block(s) beginning at offset 47710250 found in file system object FF1378496.
Inode F1378496 has references to cross linked blocks.
Directory entries for unallocated files have been detected.  Will remove.
**Phase 4 - Report Problems
File system object FF184828 is linked as: /home/leon/.kde4/share/apps/konqueror/faviconrc
The path(s) refer to an unallocated file. Will remove.
Fileset object FF1251585:  No paths found.
File claims cross linked block(s).
cannot repair FF1251585.  Will release.
Fileset object FF1251596:  No paths found.
File claims cross linked block(s).
cannot repair FF1251596.  Will release.
File system object FF1251600 is linked as: /home/leon/.kde4/share/config/session/dolphin_1010413d143151000121263462900000065410017_1212640858_803312
The path(s) refer to an unallocated file. Will remove.
File system object FF1251604 is linked as: /home/leon/.kde4/share/config/session/kwin_1010413d143151000120645504200000060110000_1212640859_120447
The path(s) refer to an unallocated file. Will remove.
File system object FF1251605 is linked as: /home/leon/.kde/share/config/akregatorrc
The path(s) refer to an unallocated file. Will remove.
File system object FF1251607 is linked as: /home/leon/.kde4/share/config/ksmserverrc
The path(s) refer to an unallocated file. Will remove.
File system object FF1251611 is linked as: /home/leon/Documents/College/Senior/Thesis/thesis/presentation/afterevaporation.png
File claims cross linked block(s).
cannot repair FF1251611.  Will release.
File system object FF1251627 is linked as: /home/leon/Documents/College/Senior/Thesis/thesis/presentation/afterevaporation.eps
File claims cross linked block(s).
cannot repair FF1251627.  Will release.
File system object FF1251639 is linked as: /home/leon/Documents/College/Senior/Thesis/thesis/presentation/beforetunneling.eps
File claims cross linked block(s).
cannot repair FF1251639.  Will release.
Fileset object FF1253212:  No paths found.
File claims cross linked block(s).
cannot repair FF1253212.  Will release.
File system object FF1308000 is linked as: /home/leon/.mozilla/firefox/mzj2t2r3.default/Cache/844A99F2d01
File claims cross linked block(s).
cannot repair FF1308000.  Will release.
File system object DF1336016 is linked as: /home/leon/.kde4/share/apps/konqueror
File system object FF1378496 is linked as: /var/tmp/kdecache-leon/http/a/www.astro.lsa.umich.edu_obs_mdm_pictures_thumbnails_Dscn0126.jpg_039f6e05
File claims cross linked block(s).
cannot repair FF1378496.  Will release.
File system object DF1384781 is linked as: /home/leon/Documents/College/Senior/Thesis/thesis/presentation
Fileset object FF1385910:  No paths found.
File claims cross linked block(s).
cannot repair FF1385910.  Will release.
File system object DF1476224 is linked as: /home/leon/.kde4/share/config/session
File system object FF1851595 is linked as: /home/leon/.kde/share/apps/akregator/lock
File claims cross linked block(s).
cannot repair FF1851595.  Will release.
File system object FF1851701 is linked as: /home/leon/.kde/share/config/kpgprc
The path(s) refer to an unallocated file. Will remove.
File system object FF1851866 is linked as: /home/leon/.kde4/share/config/kdeglobals
The path(s) refer to an unallocated file. Will remove.
File system object FF1851869 is linked as: /home/leon/.kde4/share/config/kwinrc
The path(s) refer to an unallocated file. Will remove.
File system object FF1851880 is linked as: /home/leon/.kde4/share/config/plasmarc
The path(s) refer to an unallocated file. Will remove.
File system object FF1955690 is linked as: /home/leon/Documents/College/Senior/Thesis/thesis/leon.zip
File claims cross linked block(s).
cannot repair FF1955690.  Will release.
File system object DF1984384 is linked as: /home/leon/.mozilla/firefox/mzj2t2r3.default/Cache
File system object DF2081716 is linked as: /home/leon/Documents/College/Senior/Thesis/thesis/leon
Directory claims cross linked block(s).
cannot repair DF2081716.  Will release.
**Phase 5 - Check Connectivity
No paths were found for inode F992885.
**Phase 6 - Perform Approved Corrections
Superblock marked dirty because repairs are about to be written.
Directory inode F184338 entry reference to inode F1251607 removed.
Directory inode F184338 entry reference to inode F1851866 removed.
Directory inode F184338 entry reference to inode F1851869 removed.
Directory inode F184338 entry reference to inode F1851880 removed.
Directory inode F456556 entry reference to inode F1851595 removed.
Directory inode F937914 entry reference to inode F1251605 removed.
Directory inode F937914 entry reference to inode F1851701 removed.
Directory inode F1085647 entry reference to inode F1378496 removed.
Storage allocated to inode F1251585 has been cleared.
Storage allocated to inode F1251596 has been cleared.
Storage allocated to inode F1251611 has been cleared.
Storage allocated to inode F1251627 has been cleared.
Storage allocated to inode F1251639 has been cleared.
Storage allocated to inode F1253212 has been cleared.
Storage allocated to inode F1308000 has been cleared.
Directory inode F1336016 entry reference to inode F184828 removed.
Storage allocated to inode F1378496 has been cleared.
Directory inode F1384781 entry reference to inode F1251639 removed.
Directory inode F1384781 entry reference to inode F1251627 removed.
Directory inode F1384781 entry reference to inode F1251611 removed.
Storage allocated to inode F1385910 has been cleared.
Directory inode F1476224 entry reference to inode F1251604 removed.
Directory inode F1476224 entry reference to inode F1251600 removed.
Storage allocated to inode F1851595 has been cleared.
Link count for inode F1953810 has been adjusted/corrected.
Directory inode F1953810 entry reference to inode F1955690 removed.
Directory inode F1953810 entry reference to inode F2081716 removed.
Storage allocated to inode F1955690 has been cleared.
Directory inode F1984384 entry reference to inode F1308000 removed.
Storage allocated to inode F2081716 has been cleared.
File inode  2081795 has been reconnected to /lost+found/.
File inode  2081771 has been reconnected to /lost+found/.
File inode  2081767 has been reconnected to /lost+found/.
File inode  2081727 has been reconnected to /lost+found/.
File inode  2081726 has been reconnected to /lost+found/.
File inode  2081725 has been reconnected to /lost+found/.
File inode  2081724 has been reconnected to /lost+found/.
File inode  2081723 has been reconnected to /lost+found/.
File inode  2081722 has been reconnected to /lost+found/.
File inode  2081721 has been reconnected to /lost+found/.
File inode  2081720 has been reconnected to /lost+found/.
File inode  2081717 has been reconnected to /lost+found/.
File inode  992885 has been reconnected to /lost+found/.
13 files reconnected to /lost+found/.
**Phase 7 - Rebuild File/Directory Allocation Maps
**Phase 8 - Rebuild Disk Allocation Maps
Filesystem Summary:
Blocks in use for inodes:  152568
Inode count:  1220544
File count:  1030884
Directory count:  29312
Block count:  50331648
Free block count:  11023191
201326592 kilobytes total disk space.
   396548 kilobytes in 29312 directories.
156448398 kilobytes in 1030884 user files.
   235936 kilobytes in extended attributes
        0 kilobytes in access control lists
   946042 kilobytes reserved for system use.
 44092764 kilobytes are available for use.
Filesystem is dirty.
**** Filesystem was modified. ****
processing terminated:  6/7/2008 12:27:27  with return code: 0  exit code: 4.

```

Any thoughts on what might be causing my problem and what I should do? If it's a hardware problem, that can be replaced. If it's a software problem, I can change the software. If the partition has simply been damaged beyond repair, I can simply reformat it. But I could use some advice for where to start.

---

### Post by fjgaude on 2008-06-10
From the fsck it sure looks like a flaky drive, one going bad because of bad sectors.

---

### Post by dlenmn on 2008-06-10
fjgaude, thanks for the reply. I would have expected the RAID to complain if a disk was going south, but I can believe that it could miss it. However, there are a number of other partitions on the array (including a Windows XP install) and none of them have given me any trouble, and I would have expected problems from them if a drive was dieing. Thanks.

---

### Post by fjgaude on 2008-06-10
Well, "cross linked blocks" sure point to that section of a drive as not too good.

Drives that were not made with glass platters tended to slowly give up the ghost because of thermal stress over time, the sputtered iron oxide not having exactly the same temperature coefficient of expansion as the aluminum that the platters were made of. If your drive is old enough you have aluminum platters, not glass where the coefficients can be made the same.

Good luck with your issues.

---

### Post by articpenguin on 2008-06-13
cross-linked files are files which are on the same block. Thats bad as each block can only have one file. Reminds me of fat32. I think JFS is not reliable/

---

