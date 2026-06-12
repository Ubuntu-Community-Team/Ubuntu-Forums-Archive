---
title: "Permissions problem for root, reiserfs, corruption"
date: 2013-06-25
forum: General Help
---

### Post by kuangmk11 on 2013-06-25
I had a power failure last night.  I rebooted and everything looked ok.  I started my nightly backup scripts that failed to run because of the outage and the filesystem crashed halfway through causing/caused by a corruption on one of my home servers drives.  I recently did a fresh install of 12.04 Server and everything was up to date and no funny business.  The problem disk is a hitachi 1 TB drive formatted with reiserfs.  
first I did a:
```
reiserfsck --check --logfile /var/log/reiserfsck-dd5.2.log /dev/sde1
```
which reported :
```
bad_path: block 224788663, pointer 13: The used space (4056) of the child block (224788695) is not equal to the (blocksize (4096) - free space (44) - header size (24))
bad_leaf: block 224788825, items 2 and 3: The wrong order of items: [536342 677491 0x1 DIR (3)], [536342 677491 0x1 DIR (3)]
bad_path: The right delimiting key [536342 716003 0x18933800 DIR (3)] of the node (224788818) must be greater than the last (6) element's key [536379 692482 0x1 IND (1)] within the node.
bad_stat_data: The objectid (716004) is shared by at least two files. Can be fixed with --rebuild-tree only.
bad_stat_data: The objectid (664339) is shared by at least two files. Can be fixed with --rebuild-tree only.
bad_indirect_item: block 224788862: The item (536361 664339 0x1 IND (1), len 20, location 1048 entry count 0, fsck need 0, format new) has the bad pointer (0) to the block (176330830), which is in tree already
bad_indirect_item: block 224788862: The item (536361 664339 0x1 IND (1), len 20, location 1048 entry count 0, fsck need 0, format new) has the bad pointer (1) to the block (176330831), which is in tree already
bad_indirect_item: block 224788862: The item (536361 664339 0x1 IND (1), len 20, location 1048 entry count 0, fsck need 0, format new) has the bad pointer (2) to the block (176330832), which is in tree already
bad_indirect_item: block 224788862: The item (536361 664339 0x1 IND (1), len 20, location 1048 entry count 0, fsck need 0, format new) has the bad pointer (3) to the block (176330833), which is in tree already
bad_indirect_item: block 224788862: The item (536361 664339 0x1 IND (1), len 20, location 1048 entry count 0, fsck need 0, format new) has the bad pointer (4) to the block (176330834), which is in tree already
bad_stat_data: The objectid (692482) is shared by at least two files. Can be fixed with --rebuild-tree only.


``` 
so I did a:
```
reiserfsck --rebuild-tree --logfile /var/log/reiserfsck-rebuildtree-dd5.log /dev/sde1
```
which reported:
```
####### Pass 0 #######
block 43748863: The number of items (256) is incorrect, should be (1) - corrected
block 43748863: The free space (8204) is incorrect, should be (4048) - corrected
pass0: vpf-10210: block 43748863, item 0: The item with wrong offset or length found [18874881 50405376 0x4012008000000 DRCT (2)], len 0 - deleted
block 56456847: The number of items (1) is incorrect, should be (0) - corrected
block 56456847: The free space (1) is incorrect, should be (4072) - corrected
block 56589358: The number of items (47) is incorrect, should be (1) - corrected
block 56589358: The free space (65524) is incorrect, should be (2000) - corrected
pass0: vpf-10110: block 56589358, item (0): Unknown item type found [3959423016 409008643 0x4000003 ??? (15)] - deleted
block 93524524: The number of items (514) is incorrect, should be (1) - corrected
block 93524524: The free space (288) is incorrect, should be (4048) - corrected
pass0: vpf-10110: block 93524524, item (0): Unknown item type found [514 18874882 0x2020003 ??? (15)] - deleted
block 118931684: The number of items (768) is incorrect, should be (1) - corrected
block 118931684: The free space (8212) is incorrect, should be (4048) - corrected
pass0: vpf-10110: block 118931684, item (0): Unknown item type found [197184 538182400 0x1200201 ??? (15)] - deleted
block 174995725: The number of items (11) is incorrect, should be (0) - corrected
block 174995725: The free space (0) is incorrect, should be (4072) - corrected
pass0: block 224788825, 2 (upper): Item [536342 677491 0x1 DIR (3)] is out of order - deleted
221970 directory entries were hashed with "r5" hash.
####### Pass 1 #######
####### Pass 2 #######
####### Pass 3 #########
vpf-10680: The file [526993 528640] has the wrong block count in the StatData (2200) - corrected to (2192)
rebuild_semantic_pass: The entry [714706 714904] ("Picasa.ini") in directory [714700 714706] points to nowhere - is removed
rebuild_semantic_pass: The entry [714706 714906] ("springscoot2.jpg") in directory [714700 714706] points to nowhere - is removed
rebuild_semantic_pass: The entry [714706 714907] ("springscoot3.jpg") in directory [714700 714706] points to nowhere - is removed
rebuild_semantic_pass: The entry [714706 714905] ("Thumbs.db") in directory [714700 714706] points to nowhere - is removed
vpf-10650: The directory [714700 714706] has the wrong size in the StatData (176) - corrected to (48)
rebuild_semantic_pass: The entry [714702 714823] ("small_IMG_2201.JPG") in directory [543481 714702] points to nowhere - is removed
rebuild_semantic_pass: The entry [714702 714824] ("small_IMG_2387.JPG") in directory [543481 714702] points to nowhere - is removed
vpf-10680: The file [714702 714822] has the wrong block count in the StatData (8) - corrected to (0)
vpf-10650: The directory [543481 714702] has the wrong size in the StatData (160) - corrected to (80)
rebuild_semantic_pass: The entry [714704 714895] ("Picasa.ini") in directory [545022 714704] points to nowhere - is removed
rebuild_semantic_pass: The entry [714704 714896] ("Thumbs.db") in directory [545022 714704] points to nowhere - is removed
vpf-10650: The directory [545022 714704] has the wrong size in the StatData (112) - corrected to (48)
rebuild_semantic_pass: The entry [714703 714849] ("Picasa.ini") in directory [543483 714703] points to nowhere - is removed
rebuild_semantic_pass: The entry [714703 714850] ("Untitled-10.jpg") in directory [543483 714703] points to nowhere - is removed
rebuild_semantic_pass: The entry [714703 714851] ("Untitled-16.jpg") in directory [543483 714703] points to nowhere - is removed
vpf-10650: The directory [543483 714703] has the wrong size in the StatData (144) - corrected to (48)
vpf-10680: The directory [536342 716003] has the wrong block count in the StatData (4) - corrected to (19)
vpf-10650: The directory [536342 716003] has the wrong size in the StatData (1848) - corrected to (9688)
rebuild_semantic_pass: The entry [536342 545599] ("2007-11-22 Engagement anouncement") in directory [536342 692932] points to nowhere - is removed
rebuild_semantic_pass: The entry [536342 546521] ("2008-09-06 kim's last night") in directory [536342 692932] points to nowhere - is removed
vpf-10650: The directory [536342 692932] has the wrong size in the StatData (424) - corrected to (320)
####### Pass 3a (lost+found pass) #########
get_next_directory_item: The entry ".." of the directory [536342 716007] pointes to [536342 545599], instead of [2 4] - corrected

```

Seemed like everything went well, so I remounted the drive.  That's when I noticed that the main "files" directory in the root of the drive was missing from the share.
```
root@gargoyle2:/storage/dd5# ls -l
ls: cannot access files: Permission denied
total 2258120
-rwxrwxrwt  1 root root 2297516289 Jun 16 12:43 backup.tar.bz2
-rwxrwxrwt  1 root root   12531101 Jun 16 10:32 etc.tar.gz
??????????  ? ?    ?             ?            ? files
drwxrwxrwx  3 root root       4912 Jun 25 11:43 lost+found
drwxrwsrwt 34 ono  root       1080 Jun 23 10:33 portable_apps

root@gargoyle2:/storage/dd5# chown root:root files
chown: cannot access `files': Permission denied

root@gargoyle2:/storage/dd5# chmod 777 files
chmod: cannot access `files': Permission denied


root@gargoyle2:/storage/dd5# lsattr files
lsattr: Permission denied while trying to stat files


```

Note the funny tick in "`files'".  Is there anything I can do?  I have an offline backup from before my re-install that I can restore, but I have made a bunch of changes to the structuring that will need to be redone.

Found a similar threads here: 
[http://ubuntuforums.org/showthread.php?t=1301116](http://ubuntuforums.org/showthread.php?t=1301116)
[http://forums.gentoo.org/viewtopic-t-540419-start-0.html](http://forums.gentoo.org/viewtopic-t-540419-start-0.html)

I have rebooted it.  both restart and full power down.


edit: fsck reports it wants to rebuild the tree again so doing that now.

---

