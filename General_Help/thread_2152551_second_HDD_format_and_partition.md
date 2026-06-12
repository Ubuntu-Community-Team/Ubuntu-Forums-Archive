---
title: "second HDD format and partition?"
date: 2013-06-08
forum: General Help
---

### Post by virtdave@mcn.org on 2013-06-08
I just installed Ubuntu 12.04 on a new Sedatech desktop.  It has two hard drives, a 60GB SSD SATA3 and a 500GB SATA2.  Ubuntu is using only the SSD, identified in the Disk Utility as /dev/sda, and it's about 20% full now.   The other drive does not seem to be being used--Disk Utility identifies it as /dev/sdb, and tells me it's not partitioned.  How should I format and partition it so Ubuntu will recognize and how can I make Ubuntu use it as well as the SSD?
Otherwise, Ubuntu is working extra well.....

---

### Post by benzarti on 2013-06-08
You can use the GUI tool GParted, in terminal do:
sudo apt-get install gparted

---

### Post by CatKiller on 2013-06-08
As for how to use it, the most common configuration for a second partition is to have /home there.

---

### Post by virtdave@mcn.org on 2013-06-08
hmm..../dev/sdb (the as-yet unformatted 500GB disk) does not appear in GParted.  It does show up in Disk Utility, where the bar showing the Volume is greyed out (and says 'Unknown 500Gb), and includes an option Format Drive (with a pull-down menu with choices Master Boot Record, GUID Partition Table, Don't Partition, and Apple Partition Map), and an option Format Volume (with a pull-down menu with lotsa choices--the default seems to be Ext4, but there's also NTFS, Ext2, Ext3, btrfs, FAT, XFS, Swap Space, and Empty)....which of these should I use, and in what order?  Do I format the drive first, then format the volume?

---

### Post by benzarti on 2013-06-08
You choose Master Boot Record for format drive. You choose ext3fs or ext4fs for format volume.

---

### Post by oldfred on 2013-06-08
If it is a new system, are you booting from SSD in UEFI mode or BIOS mode? If UEFI then drive will be gpt partitioned, but Ubuntu can boot from gpt partitioned drives with BIOS also. 
You should use the same partitioning on both drives or use the gpt partitioning. I have an old XP with MBR(msdos) partitioning and several other drives with Ubuntu using gpt partitioning. But XP is so old it cannot read a NTFS formatted partition on a gpt drive.

You can set up 500GB as data drive and mount partition(s) into your /home to use directly. Details and discussion in these threads.
       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by virtdave@mcn.org on 2013-06-08
I think I am making some headway....using Disk Utility, I have formatted--ext4(version 1.0)-- and partitioned the 500 GB disk, which I named bigdisk...I mounted it--Disk Utility insisted it be mounted at /media/bigdisk.  But I can't open it, permission is denied.  Seems that root owns it--it's locked, and I'm hesitant to move stuff to it, if indeed I could.  Any further hints?  sorry if I'm being dense....

---

### Post by benzarti on 2013-06-08
Open terminal
```

sudo chmod 0775 /media/bigdisk

```

---

### Post by oldfred on 2013-06-08
#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER

You may want to permanently mount with fstab.

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

More info:

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by benzarti on 2013-06-08
If you haven't /home partition you can mount your second disk as /home permanently with fstab.

---

### Post by virtdave@mcn.org on 2013-06-09
> **benzarti said:**
> Open terminal
```

sudo chmod 0777 /media/bigdisk

```

I've done this, a couple of times, but when I try to read bigdisk, I am still told I don't have permission, and there's a little padlock icon on the folder when I go to /media/bigdisk.  I noticed that /media/bigdisk seems to be in the home folder, is that germane?

---

### Post by benzarti on 2013-06-09
What returns ```
sudo mount
```?

---

### Post by virtdave@mcn.org on 2013-06-09
> **benzarti said:**
> What returns ```
sudo mount
```?

a bunch of stuff about other disks, but the following regarding sdb1:

dev/sdb1 on /media/bigdisk type ext4 (rw,nosuid,nodev,uhelper=udisks)

---

### Post by benzarti on 2013-06-09
Try```

sudo cd /media/bigdisk
sudo chmod 0775 ./
sudo chown $USER:$USER ./

```

---

### Post by rewyllys on 2013-06-09
There are a number of advantages to using separate partitions for / (root) and /home.  A major one is that having a separate /home partition makes it much easier to update your OS or to change it.

You can have the separate partitions on different hard drives, or on the same hard drive if there is space for them.

---

### Post by oldfred on 2013-06-09
Did you do both the chmod and the chown?

---

### Post by virtdave@mcn.org on 2013-06-09
well.....although I still can't directly read what's in bigdisk, gparted now tells me it's in use, and that some stuff is being stored there.  I thank everyone for their input.  I don't really need to view the stuff directly, but I am gonna assume that Ubuntu is now putting files that don't need quick access there, since about 7GB (out of the 500GB total available) now seems to be filled with data--and the SSD which has the boot stuff in it is now a bit less full than before I formatted bigdisk.....

---

