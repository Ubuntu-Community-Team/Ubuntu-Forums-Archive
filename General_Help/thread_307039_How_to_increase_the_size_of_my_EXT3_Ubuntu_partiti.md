---
title: "How to increase the size of my EXT3 Ubuntu partition on a dualboot..."
date: 2006-11-26
forum: General Help
---

### Post by klokwyze on 2006-11-26
I am currently using a dual boot on the same HDD.

Got Windows XP and ubuntu -dapper drake installed. Windows XP uses NTFS and Dapper uses EXT3. I want to resize my EXT3 partition to be larger @ the expense of the NTFS.

I downloaded "Gnome Partition Editor", but when I select my EXT3 partition it doesn't give me the option to resize it.

And the HDD doesn't appear AT ALL in "QTparted"

Can anyone help me out???

Thanks!!!!! ](*,)

---

### Post by taurus on 2006-11-26
You CANNOT resize a partition while it's in use.  If you want to resize it, you need to use either the LiveCD or the GParted LiveCD...  

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by LostShootingStar on 2006-11-26
[http://www.ubuntuforums.org/showthread.php?t=264608](http://www.ubuntuforums.org/showthread.php?t=264608)

> **LostShootingStar said:**
> Thanks for the reply. I was using the gparted that comes with the daper live CD, which cant move ext3. i wish i would have seen your post sooner and i would have used a gparted live CD and saved some trouble. oh welll!

anyway, i got this working last night without to much trouble. everything worked fine when i told grub to use /dev/sda4 and (hd0,3). but when i deleted /dev/sda2, grub had "error 22". so after a few min of fiddling i realized that /dev/sda2 no longer existed in the partition table, and that was confusing grub.

I noticed in gparted that when i was copy/pasting the partition, it would alternate between /dev/sda2 and /dev/sda4. so all i did was copy and paste the partition twice, to get sda2 to start where the windows partition ended. then i deleted /sda4 all together, and extended /sda2 and everything works great! a bit of a round about way I guess, but now i know for next time.

---

### Post by klokwyze on 2006-11-26
will my ubuntu 6.06 Live cd work?

---

### Post by taurus on 2006-11-26
Yip.

---

### Post by klokwyze on 2006-11-26
I realize now though I can't extend the size of the partition "before it". Cause the WIndows is the primary and the Ubuntu comes after.... ill just re-install probably....

Thanks for the help. :mrgreen:

---

### Post by CatKiller on 2006-11-26
> **klokwyze said:**
> I realize now though I can't extend the size of the partition "before it". 

From the quote in this thread:

> ...I was using the gparted that comes with the daper live CD, which cant move ext3....

If you use the [GParted live cd]("http://gparted.sourceforge.net/livecd.php") you'll be able to move the start of your ext3 partition.

> **taurus said:**
> Yip.

Naughty taurus ;)

---

