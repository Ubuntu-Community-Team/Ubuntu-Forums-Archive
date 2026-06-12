---
title: "Partitioning Error"
date: 2006-07-31
forum: General Help
---

### Post by zisme on 2006-07-31
Sorry for the lengthy explination. 

I went to install, and got up to where it asks you if you want to manually change partitions, or it to automatically do it. I wanted to set it up so I could have a shared data section. It set it up something like this:
NTFS (For XP) - Resize to 30 GB's
New Partition #1 - Extended
-----New Partition #2 - FAT 32 (For shared files)
-----New Partition #3 - Ext3 (For the /home)
-----New Partition #4 - Ext3 (For the /)
-----New Partition #5 - linux-swap (For the swap partition)

During "New Partition #4" it gave me an error, and it said this error may also affect following operations. Then it froze. I restarted, and tried to go to windows XP:
"There was an error loading the operating system"
Is the error I got.
I loaded to the Live CD (which I'm using now) and this is what it shows for the partitions:
[img]http://www.zach.liberty-host.com/images/partitions.png[/img]

Is it possible to get the Windows partition working again, with all the files still there? I made backups, but my Windows disk is missing, and I am currently doing a lot of Flash work (otherwise I'd switch to Linux completely). Thanks for your help!

Zach

---

### Post by zisme on 2006-07-31
Someone said to type "sudo fdisk -l" and this is the output (not sure if this helps...)
> Disk /dev/hda: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1      238186   120045681    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2               1           1           0+  83  Linux
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sda: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         992      999813+   6  FAT16


---

### Post by ghee22 on 2006-08-09
I am having the same issue.  my steps taken are here: [http://www.ubuntuforums.org/showthread.php?t=231423](http://www.ubuntuforums.org/showthread.php?t=231423)

Unfortunately, this is making me really hate Ubuntu.  Hate is a strong word, but rightly so for messing up my partition.  I have decided on getting this professionaly fixed with at least $200 being spent up to $500.

Let me know if you found a fix.

---

### Post by zisme on 2006-08-09
I had to do the same thing, but it only cost me $100 Canadian! I found out it's better to use GParted before you go to the install. And also, do it step by step with an hour in between, so that the drive doesn't get over worked. That's about as far as I can tell.

---

