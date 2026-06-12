---
title: "Unallocated Useless Disk Space"
date: 2014-11-27
forum: General Help
---

### Post by henryzangpokemon on 2014-11-27
I recently uninstalled Ubuntu from my Windows 7 GRUB dual-boot computer. The 300 GB that Ubuntu left behind as "unallocated disk space" will not merge with my Windows 7 drive. The "Extend Volume" button is unclickable. 

Images:  [ATTACH=CONFIG]258245[/ATTACH]

---

### Post by nerdtron on 2014-11-27
I'm not sure about other/commercial disk patitioners but you won't be able to merge the partitions on the unallocated on the left of existing partitions. If it's the other way around it's easy to merge. But as far as the windows partitioner and gparted is concerned you wont be able to merge them.

Only option here is to create a partition for the 300GB and is it as usual. Don't merge it. Unless of course, you want to reinstall windows 7.

---

### Post by yancek on 2014-11-27
I don't know if you can do that with windows but you would be better off trying to resolve the problem with your windows install at a windows forum or the microsoft support forums.

It is possible to expand to the left with GParted but given your particular situation, I wouldn't bother trying as it will lead to a number of additional problems, the most likely being an unbootable system.  Go with the suggestion by nerdtron and create another partition for your data.

---

### Post by mcduck on 2014-11-28
You can only extend partition to space after it, not before it. However you should be able to *move* the partition to use the space in front of it, and then extend it to fill the drive.

Make sure you have backups of important files, of course, any partition edits have their own risks, and since you'll need to do two operations that's also twice the risk...

---

### Post by p-bethe on 2014-12-01
I have some free space to the right of an NTFS partition which I cannot use.  Computer Management says "operation is not supported by the object" when I try try to expand into it.  I forget what Gparted said when I tried to use it to expand the NTFS partition.  Gparted is what freed up the space.  Windows is such a resource hog that I need to take some disk from linux so that I can use it in Windows.

---

### Post by p-bethe on 2014-12-01
I have some free space to the right of an NTFS partition which I cannot use. Disk Management says "operation is not supported by the object" when I try try to expand into it.  I forget what Gparted said when I tried to use it to expand the NTFS partition.  Gparted is what freed up the space.  Windows is such a resource hog that I need to take some disk from linux so that I can use it in Windows.  I notice that Disk Management calls it free space rather than unallocated.  Does anyone know the difference?

---

