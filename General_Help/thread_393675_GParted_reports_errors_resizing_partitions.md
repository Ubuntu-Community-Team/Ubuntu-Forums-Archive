---
title: "GParted reports errors resizing partitions"
date: 2007-03-26
forum: General Help
---

### Post by stchman on 2007-03-26
Hello all I havea machine that I am dual booting (XP/6.10).

The machine is a 250GB hd and the Ubuntu partition is on a 100G partition.  I am wanting to resize that 100G to a 40G and 60G partition.  The 6.10 LiveCD has GParted so I will boot into it (just like I partitioned my laptop) and resize the partition.

I resize /dev/hda3 to 40G and create a new partition with the other 60G.

I then apply the operations and here is where I get the errors.

An error occured while applying the operations

The following operation could not be applied to disk:

Resize /dev/hda3 from 103.81 GiB to 39.45 GiB

See the details for more information

I go to the more details and  I get this

check filesystem on /dev/hda3 for errors and (if possible) fix them

I then try the fsck command.  I enter this in a terminal.  Mind you I am still on the LiveCD.  As a matter of fact I am typing this post from teh LiveCD.

sudo fsck /dev/hda3

output:
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
/dev/hda3: clean, 142577/13615104 files, 1565863/27212101 blocks

I am at a bit of a loss.  Ubuntu runs absolutely fine when running the OS from /dev/hda3.

Are there other ways to check the filesystem or other options at the command line.

Thanks

---

### Post by dcstar on 2007-03-26
> **stchman said:**
> Hello all I havea machine that I am dual booting (XP/6.10).

The machine is a 250GB hd and the Ubuntu partition is on a 100G partition.  I am wanting to resize that 100G to a 40G and 60G partition.  The 6.10 LiveCD has GParted so I will boot into it (just like I partitioned my laptop) and resize the partition.

I resize /dev/hda3 to 40G and create a new partition with the other 60G.

I then apply the operations and here is where I get the errors.

An error occured while applying the operations
........
I am at a bit of a loss.  Ubuntu runs absolutely fine when running the OS from /dev/hda3.

Are there other ways to check the filesystem or other options at the command line.

Thanks

If you have "Automount" enabled then Gparted will have issues as the partitions it works on will be mounted by the Gnome desktop before it has finished working on them!

Best to disable automounting before doing any of these Gparted operations, things seem to go much smoother........      ;)

---

### Post by stchman on 2007-03-26
> **dcstar said:**
> If you have "Automount" enabled then Gparted will have issues as the partitions it works on will be mounted by the Gnome desktop before it has finished working on them!

Best to disable automounting before doing any of these Gparted operations, things seem to go much smoother........      ;)

I am using GParted from the Edgy LiveCD so no partition should be mounted.  Should it?  You cannot resize a partition that is mounted?  Correct?  Is there an automount feature on the LiveCD?

Thanks

---

### Post by zvacet on 2007-03-26
Jusr to be sure download Gparted Live CD and work with it.

---

### Post by stchman on 2007-03-26
> **zvacet said:**
> Jusr to be sure download Gparted Live CD and work with it.

I tried that and the GParted live CD won't boot.  I downloaded the .iso and burned it to a CD.  It gets to a certain point and stalls.  I waited about 10 mins and still the same thing.

---

### Post by silas_irl on 2007-03-26
> **stchman said:**
> I am using GParted from the Edgy LiveCD so no partition should be mounted.  Should it?  You cannot resize a partition that is mounted?  Correct?  Is there an automount feature on the LiveCD?

ThanksI had the exact same problem when I was installing Dapper on my laptop.  

AFAIK when you boot off the livecd it automounts your windows partitions, could be wrong but pretty sure it does. A umount on these should unmount the partitions, retry gparted then, and see if it gets you anywhere.

I didn't know this at the time, and I think I used *ntfsresize* command to resize the partition.

---

### Post by stchman on 2007-03-26
> **silas_irl said:**
> I had the exact same problem when I was installing Dapper on my laptop.  

AFAIK when you boot off the livecd it automounts your windows partitions, could be wrong but pretty sure it does. A umount on these should unmount the partitions, retry gparted then, and see if it gets you anywhere.

I didn't know this at the time, and I think I used *ntfsresize* command to resize the partition.

I will try that.  I don't want to touch the NTFS partitions at all.  I just want to make one 40G ext3 and one 60G ext3 out of a 100G ext3 partition.  I would think that the other NTFS partitions would not make a difference at all, but I am probably mistaken.

A colleague here at work says to run chkdsk /f on the windows NTFS partitions and that may correct the problem.  So would I just type umount at the terminal while running the LiveCD?  I will google it when I get home later.

If all this works I will put an entry on my website about this for others to have access to this information.

---

### Post by stchman on 2007-03-27
Ok I figured it out.  My colleague at work said to run a chkdsk /f on the Windows XP installation.  This will cause XP to locate and fix errors upon boot.

After that I was able to repartition the 100G hard drive into a 40G and a 60G.

---

