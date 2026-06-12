---
title: "won't boot - displays &quot;GRUB __&quot;"
date: 2007-01-04
forum: General Help
---

### Post by DaveRowell on 2007-01-04
Won't allow me to type anything there.
Everything worked just fine yesterday - made NO system changes.  But last night I got an out of disk space message which should have been false.  I moved a bunch of large files to a windows partition (they are there) to get space and then all seemed OK.  This morning it won't boot!

My system: 
Ubuntu 6.06 LTS automagically updated - dual boots Win XP using the Win bootloader with Grub on (hda2,0) (Ubuntu \)
1st partition - Compaq's recovery junk
2nd part - Windows C:\
3rd part - Ubuntu \
Extended partition:
  4th part - swap
  5th part - /home
  6th part - /WINLIN or K:\ shared files for both systems

Using Ext2fs Windows program I should be able to examine files on the Ubutu partitions.  The Ubuntu root partition seems to be fine but I get an error trying to access /home partition.  I take it there is something wrong with that partition.

I've "fixed" Grub on the boot partition using direction from first part of [http://ubuntuforums.org/showpost.php?p=121355&postcount=5](http://ubuntuforums.org/showpost.php?p=121355&postcount=5)  It still won't start although XP does.

How can I get Ubuntu running again?
Better yet is there any way to repair the /home partition using the live CD?

---

