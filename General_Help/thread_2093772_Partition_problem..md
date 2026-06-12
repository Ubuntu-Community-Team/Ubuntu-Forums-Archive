---
title: "Partition problem."
date: 2012-12-11
forum: General Help
---

### Post by treckez on 2012-12-11
Hey guys, first post here but have been using ubuntu for 8 months or so!

I'm having some trouble with my partitions and GParted and can't seem to find a solution online anywhere. My problem is, the storage partition as show below on the screen shot is 175GB and not 350 which I thought I allocated it as when I made it. I see the extra space is on dev/sda8 which is mounted at ' / ' 

What I want to do is merge sda6 (Storage) and sda8 together, but as they are mounted I cannot edit them, is their any simple solution for this? Cause I can't find anywhere how to unmount from / 

Screen Shot:[IMG]http://i50.tinypic.com/24486ev.jpg[/IMG]

Thanks!

---

### Post by oldfred on 2012-12-11
Welcome to the forums.

You cannot delete sda8 as / (root) is your Ubuntu install. But you can make it smaller, say 25GB. I normally do not like moving a partition's start, but you can as it will be slow copying all data. Or just reinstall. Do not queue steps even though you can. Often best to do each task and commit it.

You cannot use gparted from your install except for other drives or to review your system as all partitions have to be unmounted.
You need to use liveCD or flash drive and even then liveCD will mount swap(s) to speed things up a bit. So from liveCD click on swap and right click to remove little key icon showing it is mounted.

You do have two swaps and sda5 which does not look like it is used. You can look in fstab to see which swap is used and delete the other one. Or edit fstab with other swap's UUID if it makes more sense from a drive organization.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

    
       Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

### Post by treckez on 2012-12-11
Ah that makes sense, originally I had thought that the sda5 was my unbuntu root but obviously not! So if I reduce sda8 to say 50gb, delete sda5 and one of my swaps. Can I just then increase the size of sda6 so I don't have loads of unallocated space?

---

### Post by oldfred on 2012-12-11
Should work. 

It just is more difficult to move a start of a partition as it takes several steps. You have to first shrink from right. Then move entire partition. You just cannot shrink from the left.

Usually just moving Linux partitions does not change UUID, so everything just works, but it pays to be prepared to reinstall grub if necessary.

Resizing any NTFS partition will require NTFS repairs. The PBR or partition boot sector of every NTFS partition has the start & size info that has to match partition table. You can fix with chkdsk normally. If a boot partition other repairs may also be required. So make sure you have a good Windows repairCD or USB.

---

