---
title: "Bad sector on harddisk"
date: 2008-03-28
forum: General Help
---

### Post by reyhan on 2008-03-28
hey... i just finished run ```
fsck
``` on my harddisk this is the text i found after finished ```
/dev/sda1: recovering journal
Clearing orphaned inode 5472295 (uid=0, gid=0, mode=0100644, size=66276)
Clearing orphaned inode 2346953 (uid=1000, gid=1000, mode=0100600, size=32812)
Clearing orphaned inode 2346967 (uid=1000, gid=1000, mode=0100644, size=11714)
Clearing orphaned inode 65544 (uid=111, gid=121, mode=0100600, size=0)
Clearing orphaned inode 65543 (uid=111, gid=121, mode=0100600, size=0)
Clearing orphaned inode 65542 (uid=111, gid=121, mode=0100600, size=0)
Clearing orphaned inode 65541 (uid=111, gid=121, mode=0100600, size=0)
Clearing orphaned inode 65538 (uid=111, gid=121, mode=0100600, size=0)
Checking for bad blocks (read-only test): done                                
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -4707687 -(4707707--4707710) -(4707720--4707733) +4713889 -4713920 +4713931 -(4713934--4713939) -(4713943--4713950) +4713959 +4713961 -(4713962--4713964) +4713965 -4713968 +(4713969--4713980) +(4713988--4713990) -4713992
Fix<y>? yes

Free blocks count wrong for group #143 (20884, counted=20903).
Fix<y>? yes

Free blocks count wrong (17314976, counted=17314995).
Fix<y>? yes

Inode bitmap differences:  -2343326 +2344446
Fix<y>? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: ***** REBOOT LINUX *****
/dev/sda1: 189034/9453568 files (0.8% non-contiguous), 1561372/18876367 blocks
``` is there any bad sector on my hard disk..?

---

### Post by danwood76 on 2008-03-28
after a reboot rerun fsck and see if it displays errors.
It should pass each test.

---

### Post by reyhan on 2008-03-28
okay thanks

---

