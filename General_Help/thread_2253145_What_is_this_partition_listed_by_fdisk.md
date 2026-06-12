---
title: "What is this partition listed by fdisk?"
date: 2014-11-17
forum: General Help
---

### Post by sim085 on 2014-11-17
Hello,

I just installed Ubuntu Server Edition version 14.04.1. When arrived to the section to determine partition size I selected the option to use whole disk. This listed two partitions; /sda1 and /sda5 (swap). However now that I booted, when I enter fdisk I get the following result:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008474a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   221863935   110930944   83  Linux
/dev/sda2       221865982   234440703     6287361    5  Extended
/dev/sda5       221865984   234440703     6287360   82  Linux swap / Solaris

```

What is /dev/sda2? and how is it that it overlaps on /dev/sda5?

---

### Post by nerdtron on 2014-11-17
It is an extended partition and sda5 is the logical partition inside it.

This will show you the layout of your drive.
```
 lsblk
``` 

A hard drive can only hold 4 primary partitions and 1 extended partition (if I'm not mistaken). And an extended partition (you can think of it a similar to a marker/division point) can hold more logical partitions. Thus creating an extended will let you overcome the 4 primary partitions limit and create more than 10 (can't remember exactly how much) partitions.

---

### Post by Dennis N on 2014-11-17
sda2 is an Extended Partition:

With an MSDOS-Partition Table, you can have either:

4 primary partitions OR
3 primary partitions and 1 extended partition (type 05 = container).

The extended partition contains logical partitons located within the bounds of the extended one. The number of logical partitions is arbitrary.

Right now you have one logical partition sda5 which occupies the entire extended partiton.

See: [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by sim085 on 2014-11-17
> **nerdtron said:**
> It is an extended partition and sda5 is the logical partition inside it.

Is this normal? The standard way? How is it that the end of /dev/sda1 (221863935) is different from the start of /dev/sdb1 (221865982)?

---

### Post by coldcritter64 on 2014-11-17
> Is this normal? The standard way?
From your opening post ...
> I selected the option to use whole diskNormal/standard for when that particular option is used with the installer, so yes.
> 
 ... start of /dev/sd**b**1 (221865982)?                 Your fdisk results don't show any device "sdb"... a typo?

"sdb" **if** in use would indicate a completely separate (2nd) hard drive is being used, in which case the start/end sectors are determined by partition sizes and the drive geomtry of that 2nd drive and will differ from the 1st drive (sda).

**Edit:** going on the start block 221865982 on sda2 I now think you were referring to /dev/sda2 and NOT /dev/sdb1 as posted above. Just to check, is that correct and what you where referring to?

---

### Post by sim085 on 2014-11-17
> **coldcritter64 said:**
> 
Your fdisk results don't show any device "sdb"... a typo?.

Yes, sorry, I meant /dev/sda2

/dev/sda1 ends at 221863935 and 
/dev/sda2 start at 221865982

---

### Post by coldcritter64 on 2014-11-17
You could install gparted and have a graphical check, sometimes small parts of a drive are left blank. To do with partition alignments to cylinder heads etc. I suspect there may be a small unallocated section of drive there. Check with gparted to see it easily.
**Edit:** just noted you are on a server edition, gparted would need a desktop installed to use, may or may not be feasible.

---

### Post by oldfred on 2014-11-17
There always has been some space between partitions. With newer larger 4K drives and SSDs alignment is critical, so defaults have changed.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by sim085 on 2014-11-17
Thanks for all replies. I was just alarmed given that I saw things with fdisk which installation tool did not show me. I will read on partition options and see what is best for me. Thanks to all for the help.

---

