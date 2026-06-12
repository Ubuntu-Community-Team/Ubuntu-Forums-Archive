---
title: "Repartitioning device without deleting files"
date: 2013-02-04
forum: General Help
---

### Post by tbalestr27 on 2013-02-04
Hi,

I currently have a 100Gb partition for Ubuntu. However, after 3+ years of this, I'm finding I need a little more space. Is it possible to add an unallocated memory slot to this 100Gb without deleting anything?

---

### Post by dcstar on 2013-02-04
> **tbalestr27 said:**
> Hi,

I currently have a 100Gb partition for Ubuntu. However, after 3+ years of this, I'm finding I need a little more space. Is it possible to add an unallocated memory slot to this 100Gb without deleting anything?

Memory is RAM, it has nothing to do with disk storage.

If you want to increase the size of a partition on a disk, do a search for the many hundreds of posts which already detail this task.

---

### Post by papibe on 2013-02-04
Hi tbalestr27.

Here's a few tips:
[LIST]
[*]You can't resize/move a partition which is in use. One common way to work this out is to use a live media. For instance, the installation Ubuntu CD (option 'Try Ubuntu').
[*]One of the best tools for this job is called 'gparted', which is included on the installation CD.
[*]Increasing the size of a partition often implies to shrink, or move other existing partitions.
[*]It is always a good idea to backup your data from the affecting partitions. It all goes well, you won't lose your data. Backup is just 'in case'.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

P.S.:
> **dcstar said:**
> Memory is RAM, it has nothing to do with disk storage.
+1

Either you weren't able explain yourself well, or you are little confused. In any case, if you post more details, we may come out with more specific ideas.

---

### Post by furything on 2013-02-04
Yeah sorry to repeat but you need to add more info.

Like is this for a laptop or desktop?

If for a desktop is there room to add an extra drive?

You can easily store data on another drive or even pendrive and just access it through your file browser - the simplest way.

Have you thought about using the package manager and seeing how many old kernel images you have and cleaning down to the most recent 2?

---

