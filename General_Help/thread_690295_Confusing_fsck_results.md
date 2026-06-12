---
title: "Confusing fsck results"
date: 2008-02-07
forum: General Help
---

### Post by Dan_at_NRT on 2008-02-07
I'm getting mixed messages from e2fsck.

With the system live if I run 'e2fsck -f -n -v /dev/sda1' it reports that there are errors with the file system. Specifically it reports the information provided below. It appears I need to fix things up. I boot from my live CD and in this environment I run 'e2fsck -f -v /dev/sda1' which goes through all 5 passes without the first sign of an error. Does the filesystem have problems or not? And if it does how do I repair them?

Thanks for any help,
Dan

--------------------------------------------------------------------------------------

Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 16973826 has zero dtime.  Fix? no                                

Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 16973829 was part of the orphaned inode list.  IGNORED.
Inode 16973830 was part of the orphaned inode list.  IGNORED.
Inode 16973831 was part of the orphaned inode list.  IGNORED.
Inode 16973832 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
Block bitmap differences:  -10865691 -23558155                                 
Fix? no

Free blocks count wrong for group #331 (10212, counted=10211).
Fix? no

Free blocks count wrong for group #689 (10, counted=2).
Fix? no

Free blocks count wrong for group #703 (193, counted=202).
Fix? no

Free blocks count wrong for group #718 (22227, counted=22225).
Fix? no

Free blocks count wrong for group #1036 (32229, counted=32231).
Fix? no

Free blocks count wrong for group #1145 (22695, counted=22699).
Fix? no

Free blocks count wrong (35180747, counted=35182390).
Fix? no

Inode bitmap differences:  -5424444 +5424613 -16973826 -(16973829--16973832)   
Fix? no

Free inodes count wrong for group #1036 (16327, counted=16330).
Fix? no

Directories count wrong for group #1036 (15, counted=14).
Fix? no

Free inodes count wrong (19013018, counted=19012984).
Fix? no


/dev/sda1: ********** WARNING: Filesystem still has errors **********

/dev/sda1: 156262/19169280 files (4.8% non-contiguous), 3134270/38315017 blocks

---

### Post by oldos2er on 2008-02-07
You shouldn't run fsck on a mounted partition. A mounted partition, particularly if it's your boot partition, is going to have thousands of files open, which fsck will most likely read as errors. ALWAYS unmount a partition before running fsck.

---

