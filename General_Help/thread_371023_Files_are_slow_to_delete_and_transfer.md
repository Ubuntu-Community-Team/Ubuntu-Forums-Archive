---
title: "Files are slow to delete and transfer"
date: 2007-02-26
forum: General Help
---

### Post by TheForkOfJustice on 2007-02-26
Deleting and moving files is incredibly slow in edgy.  I use Shift+Del to bypass the trashbin and that deletes files straight away but the overall problem persists.  

This is likely due to the UUID implementation and not the window/file manger since I get this problem in Thunar (Xfce file manager) and Nautilus (GNOME file manager).

The partitions I am trying to access are in XFS which 'may' be the source of the problem.

Anyway, how do I fix the move/delete speed issues?

---

### Post by mannheim on 2007-02-27
> **TheForkOfJustice said:**
> Deleting and moving files is incredibly slow in edgy.  I use Shift+Del to bypass the trashbin and that deletes files straight away but the overall problem persists.  

This is likely due to the UUID implementation and not the window/file manger since I get this problem in Thunar (Xfce file manager) and Nautilus (GNOME file manager).

The partitions I am trying to access are in XFS which 'may' be the source of the problem.

Anyway, how do I fix the move/delete speed issues?

I think xfs is just very slow at deleting or creating large numbers of files, in recent versions of the kernel. (I'm no expert, but I think it may be in part due to write_barrier's being enabled.)

When I tried a comparison of ext3 with xfs and tried duplicating the tree /usr/share as a random sort of benchmark, ext3 took 6 minutes on my rather old machine, and xfs took 20 minutes. Similar results for deleting the tree.

---

### Post by TheForkOfJustice on 2007-02-27
> **mannheim said:**
> I think xfs is just very slow at deleting or creating large numbers of files, in recent versions of the kernel. (I'm no expert, but I think it may be in part due to write_barrier's being enabled.)

When I tried a comparison of ext3 with xfs and tried duplicating the tree /usr/share as a random sort of benchmark, ext3 took 6 minutes on my rather old machine, and xfs took 20 minutes. Similar results for deleting the tree.

I just tried changing a partition from xfs to ext3 and it took forever to create the new fs.  Would this new write_barrier option slow down fs creation as well as file writing? Can I deactivate it?  Why is it even activated in the first place??

---

### Post by mannheim on 2007-02-27
> **TheForkOfJustice said:**
> I just tried changing a partition from xfs to ext3 and it took forever to create the new fs.  Would this new write_barrier option slow down fs creation as well as file writing? Can I deactivate it?  Why is it even activated in the first place??

"write_barriers" are a feature of the xfs filesystem in recent versions. One of the problems with xfs, for some people, is that if the system crashes (perhaps because of a power outage) then xfs may lose more of your data than an ext3 filesystem would, because xfs is more aggressive about choosing when to write data the disk. The "write_barrier" thing was introduced into as a way of forcing xfs to actually write the data to the disk under some circumstances (and I don't understand this any more than I just said). So write_barriers give the xfs filesystem more safety from data loss, but at the expense of decreased performance for tasks that create or delete a lot of files. You can mount an xfs filesystem and disable the write_barrier thing using the nobarrier option: eg

```
sudo mount -o nobarrier /dev/xxxx  /mountpoint
```

where "xxxx" is your partition. But this increases the risk of data loss.

Creating an ext3 filesystem would not have anything to do with any of that. Maybe the disk is just slow for some other reason. If it is unexpectedly slow, you could check whether dma is enabled, by doing

```
sudo hdparm -I /dev/xxx
```

where "xxx" is now your disk (e.g. hdb or sda).

---

### Post by TheForkOfJustice on 2007-02-27
I'll try that but to tell you the truth it happens in my GParted 3.3 LiveCD, it happens in Ubuntu/Xubuntu (Edgy) and it occurs no mater how much data I'm moving and to where I'm moving it.  

This doesn't happen in Puppy Linux and it doesn't happen in PCLinuxOS 0.93a  

This happens irregardless if it is a USB or IDE drive I'm transferring to, be it from one partition to another on the same drive or different drives.

It happens in xfs and ext3.  As I type I'm transferring 40GB of data from an xfs partition to an ext3 partition on the same USB drive and it says it will be a 20 hour operation, which is just silly.

I am currently using Xubuntu (Edgy) and never ever had this problem in Dapper so I'm guessing it's an Edgy issue, however it also happens in the GParted LiveCD v3.3 so I have no idea what is going on exactly.

---

### Post by TheForkOfJustice on 2007-02-27
I did what you said and this was the output:

```
login@system:~$ sudo hdparm -I /dev/sda

/dev/sda:
 HDIO_DRIVE_CMD(identify) failed: Invalid argument
```

So something MUST be wrong here...

---

### Post by mannheim on 2007-02-27
> **TheForkOfJustice said:**
> I did what you said and this was the output:

```
login@system:~$ sudo hdparm -I /dev/sda

/dev/sda:
 HDIO_DRIVE_CMD(identify) failed: Invalid argument
```

So something MUST be wrong here...

Yes, my fault: hdparm is only relevant for IDE drives (I think) so will give info about "hda" and "hdb" if such disks are present, but not about others.

---

### Post by TheForkOfJustice on 2007-02-27
> **mannheim said:**
> Yes, my fault: hdparm is only relevant for IDE drives (I think) so will give info about "hda" and "hdb" if such disks are present, but not about others.

I tried transferring files using other LiveCDs and I get the same speeds. Which is odd since I think I remember this being a much faster process.

One reason for this slowness may be that I'm moving files between partitions on the same drive so data going both ways at the same time, rather in just one direction, is causing a slowdown in the transfer (or so I surmise).  

Also there are many GB worth of data I'm transferring which has an obvious effect on the time of the operation.

I'm getting rid of all of my xfs and exchanging them for ext3 and I plan to tweak them a bit to boost the speed.  I can access them from windows with the driver at [http://www.fs-driver.org/](http://www.fs-driver.org/) and I also hear that ext3 is better for deleting data irreversibly so I don't have to zero my empty space to make sure all of my old data is gone.

---

### Post by mcduck on 2007-02-27
> **TheForkOfJustice said:**
> I did what you said and this was the output:

```
login@system:~$ sudo hdparm -I /dev/sda

/dev/sda:
 HDIO_DRIVE_CMD(identify) failed: Invalid argument
```

So something MUST be wrong here...

You can't do such thing for a disk, only for a partition (like /dev/sda1) :D

---

### Post by mannheim on 2007-02-27
> **mcduck said:**
> You can't do such thing for a disk, only for a partition (like /dev/sda1) :D

Not so: hdparm will give info for disks. Eg,
```
~$ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 234441648, start = 0

```

If you specify a partition, it will give you some information about the partition also, I think. I don't know about external disks, scsi disks and so on.

---

