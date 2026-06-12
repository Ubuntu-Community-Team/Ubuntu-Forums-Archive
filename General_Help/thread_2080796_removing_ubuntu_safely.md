---
title: "removing ubuntu safely"
date: 2012-11-05
forum: General Help
---

### Post by Ishwor Shrestha on 2012-11-05
hello! I want to remove ubuntu 11.0 from my pc. I have removed ubuntu's boot loader and replaced it with window's boot loader, so my pc directly boots to windows 7. Now I have to remove the partition but I have no I idea how to remove it. I installed ubuntu alongside windows, and it automatically did the required partition.

---

### Post by Bucky Ball on 2012-11-05
Boot from the Ubuntu LiveCD (the install CD), open Gparted, the partition editor, right click an EXT* partition that belongs to Ubuntu and make sure it is unmounted then delete, also from the right click menu.

Repeat until free space where EXT* partitions were.

---

### Post by varunendra on 2012-11-07
I'd recommend to do this in Windows disk manager. Would be safer.

---

### Post by Bucky Ball on 2012-11-07
> **varunendra said:**
> I'd recommend to do this in Windows disk manager. Would be safer.

? Why? For a start, don't think Win Disk Manager will recognise EXT* partitions. The only danger would be if OP was resizing a Win, i.e. NTFS or FAT, partition or the OS partition of Win itself (other than post-XP that is) ... which they're not. ;)

---

### Post by varunendra on 2012-11-07
> **Bucky Ball said:**
> The only danger would be[COLOR=Red]** if **[/COLOR]OP was resizing a Win, i.e. NTFS or FAT, partition or the OS partition of Win itselfThat **IF** is the keyword here :)
Most often the problems caused during usage of such partitioning tools are either 'accidents' or due to 'innocence' of the user. So if the tool is run from within the desired OS, it is safer. And to delete a partition you don't have to be able to recognize it. In fact the target partitions can be more easily identified due to the fact that windows will see them as 'unknown' type. And as we all know it, windows 'feels' very happy to get rid of anything that seems 'unknown' to it ;).

---

