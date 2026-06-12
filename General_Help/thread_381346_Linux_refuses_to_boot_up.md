---
title: "Linux refuses to boot up"
date: 2007-03-10
forum: General Help
---

### Post by Ydirbut on 2007-03-10
I don't have alot to work with here, so please bare with me. Heres the problem: when my computer leaves BIOS to go into linux, the screen goes black with a little blinking underscore in the top left corner. Not very helpful, I know. But I have two questions: 1) is there some way to acess the HDDs using the Livecd? and 2) Assuming you can, does linux have something like a fixmbr command? Thanks in Advance

---

### Post by JohnPhys on 2007-03-11
As long as the partition info didn't get destroyed, you should be able to mount your partitions from a live cd just fine.  If you partition info *did* get destroyed, but the files didn't, there's a decent chance you can get them back by following (shameless self-promotion)

[http://www.ubuntuforums.org/showthread.php?t=370121](http://www.ubuntuforums.org/showthread.php?t=370121)

You can use Gparted in the livecd to check if your partitions still exist (if Gparted detects them, they exist).  If this is the case, you may only have to reinstall grub to the mbr.

---

