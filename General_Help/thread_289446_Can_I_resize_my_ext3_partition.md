---
title: "Can I resize my ext3 partition?"
date: 2006-10-31
forum: General Help
---

### Post by morgue on 2006-10-31
if so, how? 

When I use live cd I don't get resize as an option :confused:

---

### Post by Sef on 2006-10-31
Get [Gparted]("http://gparted.sourceforge.net/").  It has a graphical partitioner.

---

### Post by ansi on 2006-10-31
> **morgue said:**
> if so, how? 

When I use live cd I don't get resize as an option :confused:

Yes, of course, you can. As variant, you can use for it [QtParted]("http://qtparted.sourceforge.net"), which exists in Ubuntu repository.

---

### Post by morgue on 2006-10-31
> **Sef said:**
> Get [Gparted]("http://gparted.sourceforge.net/").  It has a graphical partitioner.

Ok now how do I do it? I can't unmount the hard drive I'm on can I? :confused:

---

### Post by morgue on 2006-10-31
OK I had to disable Swap, move it.
Restart with live cd.
Resize ext3.
Restart normally.

Almost done, I want to move ext3 now... Why can I have only 4 partitions though? :confused:

---

### Post by cotcot on 2006-10-31
You can only have 4 partitions if they are "primary" or "extended". You want more ? Then "logical" partitions are the solution. Create an "extended" partition. Within the "extended" partition you can create many "logical" partitions.

I always use the Gparted LiveCD for modifications on partitions except for moving hem. It is more reliable.
For moving your ext3 I would use "parted" from the command line. "move" is well explained in the Parted manual : [http://www.gnu.org/software/parted/manual/parted.html#move]("http://www.gnu.org/software/parted/manual/parted.html#move"). There you will see that you can only move a partition to an unallocated place on your disk. Take care with the partition numbering when you move a partition to unallocated space after other partition (partition numbering is affected).

---

### Post by morgue on 2006-10-31
> **cotcot said:**
> You can only have 4 partitions if they are "primary" or "extended". You want more ? Then "logical" partitions are the solution. Create an "extended" partition. Within the "extended" partition you can create many "logical" partitions.

I always use the Gparted LiveCD for modifications on partitions except for moving hem. It is more reliable.
For moving your ext3 I would use "parted" from the command line. "move" is well explained in the Parted manual : [http://www.gnu.org/software/parted/manual/parted.html#move]("http://www.gnu.org/software/parted/manual/parted.html#move"). There you will see that you can only move a partition to an unallocated place on your disk. Take care with the partition numbering when you move a partition to unallocated space after other partition (partition numbering is affected).

Will I need a calculator for command move? hehehe

---

