---
title: "Disk errors"
date: 2007-06-23
forum: General Help
---

### Post by anafshalom on 2007-06-23
I ran fsck on my root file system in read only mode, and errors were reported.   How can I fix them if I cannot do fsck on a mounted volume?
Is this problem serious?

Here is the output:
root@Damita-Ubuntu:/home/damita# fsck.ext3 -n /dev/hda1
e2fsck 1.39 (29-May-2006)
Warning!  /dev/hda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/hda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (1203823, counted=1218729).
Fix? no

Free inodes count wrong (860144, counted=861773).
Fix? no


/dev/hda1: ********** WARNING: Filesystem still has errors **********

/dev/hda1: 125616/985760 files (0.6% non-contiguous), 766139/1969962 blocks

---

### Post by pizzutz on 2007-06-23
You can run fsck on the root partition if it is mounted read-only.  It is the one exception to the rule.

Normally you wouldn't run fsck on a mounted volume because if the system writes to it while fsck is running, it could cause major problems.  since the system can't write to it when it is mounted read-only, you will be ok.

---

