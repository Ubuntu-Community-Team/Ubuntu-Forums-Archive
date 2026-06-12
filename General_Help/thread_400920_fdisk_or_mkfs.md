---
title: "fdisk or mkfs?"
date: 2007-04-04
forum: General Help
---

### Post by carverj on 2007-04-04
Hi there,
             I am attempting to format a hard drive and have got as far as deleting partitions, but when I try to add partitions, it asks for first block ( I give default 1) and last cylinder block (default of last 1467).This seems to take up all available space as when I try to add a partition 2 there is no room left (I assume this is in the part. table as we are are talking about just 100's of blocks of data),  I can also select command o  to create empty dos partition table.
So my question is, if I am actually successfully emptying table and formatting successfully, could I then use the following commands in terminal to install any linux OS?
sudo mkfs.ext3 -b 1467*4=5868 /dev/hda1
sudo mkfs.Swap/Solaris 5868 /dev/hda2
and maybe a home partition
sudo mkfs.ext3 -b 5868 /dev/hda3
Cheers for helping

---

### Post by kidders on 2007-04-04
Hi there,

> **carverj said:**
> it asks for first block ( I give default 1) and last cylinder block (default of last 1467).This seems to take up all available spaceThat's fdisk's (and most other partition editors') default behaviour. If you're not comfortable with fdisk, there are plenty of more elabourate disk partitioners available. **cfdisk** is an example of a terminal-based one, that is slightly less obtuse.

> **carverj said:**
> could I then use the following commands in terminal to install any linux OS?The commands you posted format filesystems. Installing an OS from the command line is a complex & lengthy procedure.

Bear in mind that partitioning disks & formatting filesystems are not the same thing, and have nothing at all to do with eachother. To make a space on a disk where you can put files, you need to do both ... but carefully ... they are very destructive commands!

**fdisk** is for partition creation.
**mkfs** is for filesystem creation.

---

### Post by coxy on 2007-04-04
You can specify the size of a partition using fdisk.

```

d to delete any existing partitions (I am gussing you have no data on the disc)

n to create a new partition

p to make it primary

1 so it is the first primary partition

Accept the default or type 1 to start from the first cylinder
Then type +XXXM where XXX is the size of partition you want in MB (+1024M would be 1 GB)

t to change the partition type (83 is a Linux partition)

Repaeat the process to create more partitions

w to write changes

```

You can then use mkfs to create your file systems without having to specify block sizes.

---

