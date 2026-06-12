---
title: "Ran out of space on EXT3 filesystem, now there are filesystem errors"
date: 2007-08-12
forum: General Help
---

### Post by Super TWiT on 2007-08-12
I ran out of space on my EXT3 file system and after deleting files from it with the live CD it still says zero bytes left.  I checked it with fsck and it said that there are file system errors on it.  What should I do now?

---

### Post by prince_niceguy on 2007-08-12
Try to boot into the original OS directly. fsck will run and correct if there are errors. Hope you have not deleted any critical files from the live cd. :)

---

### Post by Super TWiT on 2007-08-15
Thanks for replying!:KS  For some reason my computer now has some free space so I am able to log back .:-k   When I run fsck in Ubuntu it does find errors, however when I can't fix the errors because the file system is mounted and I can't unmount it because it is the root file system.  When I check for errors using Gparted or the live CD they don't find any errors.  Should I run fsck in Ubuntu even though the root file system is mounted?

P.S. The files that I deleted were personal files.

---

### Post by kayvortex on 2007-08-15
You can type 

```
sudo tune2fs -c 1
```

to change the number of times the disk is mounted between a forced fsck to one. fsck will then be run when you next reboot the system. Afterwards, you can change the number back to thirty (or anything you want).

---

### Post by Super TWiT on 2007-08-15
Thanks for replying!:KS  Fsck runs when I start the computer, but it doesen't correct errors.  It says I have 121.7 MB when I should have at least 1 GB.  Here's what I get when I run e2fsck in the command line in read-only mode:```
e2fsck 1.40-WIP (14-Nov-2006)
Warning!  /dev/sda4 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (159055, counted=189809).
Fix? no

Free inodes count wrong (1529461, counted=1529452).
Fix? no


/dev/sda4: ********** WARNING: Filesystem still has errors **********

/dev/sda4: 461579/1991040 files (6.0% non-contiguous), 3806991/3966046 blocks
```

---

### Post by kayvortex on 2007-08-15
According to e2fsck's man page, its results won't be valid on a file system that is mounted. If fsck reports no problems when ran during the booting process I guess we have to trust it. Did you run fsck from the live CD while the fs was mounted? If so, try running fsck again without mounting it.

---

### Post by Super TWiT on 2007-08-16
When I ran fsck from the Live CD the file system was unmounted.  Disk Usage Analyzer says I have 1.5 GB free while Nautilus says I have 871 MB free.  Where could the 529 MB have gone?:confused:

---

### Post by Super TWiT on 2007-08-20
Could it be the 5% of disk space that Ubuntu keeps for itself on an ext3 file system?

---

### Post by kayvortex on 2007-08-20
I haven't used Disk Usage Analyzer myself, but I don't think that's likely (but I may be wrong). What does 'df' say? Type

```
df -h /
```

to view the root fs size, and how much of it is used.

Also, make sure you are comparing like for like: i.e. make sure you don't compare the root fs with the whole disk (Disk Usage Analyzer shows the whole disk by default).

---

### Post by Super TWiT on 2007-08-21
Thanks for replying!:KS  Here's what df -h / says:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              15G   14G  856M  95% /
```

---

### Post by vanadium on 2007-08-21
sda4 is probably not your main system disk. make sure that you free some space on that drive and do not worry about a difference between df and what nautilus reports. If a fscheck does not anymore report errors, everything is fine. You should not exceed 70% - 80% of the disk capacity for a disk that is dynamically used. For almost full disks, fragmentation becomes an issue and in fact, Linux cannot handle very well situations where you run out of disk space. It would be different for an archive disk, i.e. where you just store, and do not continuously delete and create files.

---

### Post by kayvortex on 2007-08-21
It is reassuring that df and nautilus both agree (assuming you have used a further 15Mb since you last posted free space figures).

Where are you getting the figure of 1.5Gb of free space in Disk Usage Analyzer (DUA)? When you start up DUA it will analyze your whole disk, not just the partition of the disk that Ubuntu lies on. In contrast, nautilus will display the free space remaining on the Ubuntu partition and just ignores the rest of your disk. I think that you may be comparing different things, in which case I don't think there is a problem with your system. Is this so?

---

