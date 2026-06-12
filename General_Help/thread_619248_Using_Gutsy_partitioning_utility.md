---
title: "Using Gutsy partitioning utility"
date: 2007-11-21
forum: General Help
---

### Post by hoosemon61 on 2007-11-21
I'd like to use the partition utility on the gutsy live cd to resize my existing partitions.  My C partition is currently too small and I'm getting errors.  I have a 160 GB drive with C: D: & E: partitions.  I could easily steal 10 GB each from D: & E:.  

I ran the utility and have a couple questions:

I set it up to reduce the size of the D: partition (no problem), but it wouldn't let me make the c: partition larger.  Is that because the D: resize was still pending and the space hadn't actually been freed up yet?


It recognized the E: partition, including total size, but did not show "used" or "free" space as with the other partitions.  It also didn't offer me the option of resizing that partition.  Why?

Thanks for any help you can offer,

Hoosemon

---

### Post by bingoUV on 2007-11-21
You are most likely colliding with the extended partition. Give the output of 
```

sudo /sbin/fdisk -l

```

---

### Post by dabl on 2007-11-21
Is your "E:" a FAT32 file format or something like that? GParted has some limitations on reading and formatting to FAT32 and NTFS.

In general, you want to run "Disk Cleaner" and then immediately "Disk Defragmenter" in Windows, and run the defragmenter 3 or 4 times to achieve minimum space utilization, prior to using GParted to re-partition, when you intend to reduce the "C:" partition.

YES, you must create "unallocated space" before it will let you expand a partition, and you have to start from the "right side" (as per the graphic bar) and work your way to the left.  The "commanded changes" don't actually execute until you are ready to execute the entire batch, with the "Apply" button.  :)

---

### Post by hoosemon61 on 2007-11-21
All are actually NTFS partitions on the same physical drive.

I'll have to reboot to the cd to see what output I get from that command.  

I guess I'll try reducing D: and then try to increase C: with the space that's freed up.  

Thanks for the suggestion to defrag and clean up first, good idea.

Hoosemon

---

### Post by hoosemon61 on 2007-11-21
> **bingoUV said:**
> You are most likely colliding with the extended partition. Give the output of 
```

sudo /sbin/fdisk -l

```



Here's what I Got:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56865686

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/hda2            2433       19457   136753312+   f  W95 Ext'd (LBA)
/dev/hda5            4359        9727    43126492+   7  HPFS/NTFS
/dev/hda6            9728       19457    78156193+   7  HPFS/NTFS


I was able to reduce the size of D: and show a 15GB unallocated space on the drive, shown between C: & D: in the graphic display of GParted.  It won't allow me to add that unallocated space to the C: partition however.

I'm guessing it has something to do with D: & E: being part of the "Extended" partition but don't really know what that means.

Any idea how I can increase C:  ?


Hoosemon

---

### Post by bingoUV on 2007-11-21
You are right, it is because you are colliding with the extended partition. 

1. Move hda5 towards beginning (left), so that it starts where extended partition hda2 starts i.e. 2433.
2. Move hda6 left, so that it starts where hda5 ends.
3. Now move the extended partition hda2 to the right, so that it ends where your hard disk ends.
4. Now you will see the option to increase the size of hda1.

---

### Post by hoosemon61 on 2007-11-21
OK,

I can't seem to move or resize my E: partition at all.  

There's a little warning sign and if I check the info related to E: I get the following:

(I can't copy it so I'm just going to type the parts that look significant)

**[INDENT]*Cluster accounting failed at 153490544 (0x9261479): extra cluster in $Bitmap*[/INDENT]**
same line repeated for 153490545 through 553.


[INDENT]***Filesystem check failed! Totally 43042 cluster accounting mismatches**.*

***ERROR: NTFS is inconsistent. Run Chkdsk /f on windows, then reboot it TWICE**!*

***The usage of the /f parameter is very important! no modification was and will be made to NTFS by this software until it gets repaired**.*
[/INDENT]
I defragged this drive twice and it's still the same.

I tried running chkdsk /f from the "run" command line in Windoze but to no avail.

Any idea what's up with this partition?

Hoosemon

---

### Post by hoosemon61 on 2007-11-21
Well, I never figured out why GParted doesn't like my E: partition, but it didn't matter.

I was able to shove my newly shrunk D: partition to the right, then move the starting edge of the extended partition to the right as well and it gave me room to grow the C: partition.

Thanks for the help!

Have a great Thanksgiving if you're celebrating.

Hoosemon

---

### Post by bingoUV on 2007-11-21
Is this drive accessible read write on windows? I don't know much about windows but can you do something like fsck? i.e. file system integrity check by windows? See if it gives any errors / warnings.

I know this is no solace to you, but let us learn from this incident and pledge to move to more open filesystems (ext2/3) in the long term.

---

### Post by hoosemon61 on 2007-11-25
The E: partition that GParted doesn't like works fine under windoze.  I've had no problems with it and don't understand the error I get.  I use it primarily for data, so I manually save and delete to and from that part of the drive more than the others.  I don't really understand the error message and the reference to a bitmap was most confusing.

Anyway, I managed to accomplish what I wanted to, so other than some mild curiosity about my E: partition, I consider this thread resolved.  

Thanks for the help everyone. 

Hoosemon

---

