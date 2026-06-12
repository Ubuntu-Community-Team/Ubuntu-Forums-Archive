---
title: "Revoming grub without a partition?"
date: 2008-03-09
forum: General Help
---

### Post by crhis on 2008-03-09
Ok, I (think) that I removed linux from my desktop, but grub is still there. I need to unistall it, how? I would also like to restore my hdd. It says that i have 3 partitions, 1 74 gb and 2 1.4 gb(i think those two have something to do with linux or grub).  I went to system > administation > partition editor, but i cant restore it back to 1 partition. Please help, i really want to turn this old computer into a dvr.

---

### Post by Rocket2DMn on 2008-03-09
To get rid of GRUB, you need to boot from your windows disc and enter the recovery console where you run
```
fixmbr
```
To get your partitions back in order, boot from the LiveCD and run the Partition Editor.  There you can delete the existing partitions and "grow" your windows partition back if you have one.  Otherwise you just delete all the partitions, then install whatever OS you want in that empty space.

You can also use the GParted LiveCD instead of the Ubuntu LiveCD (it is a much smaller download) - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by forrestcupp on 2008-03-09
> **Rocket2DMn said:**
> To get rid of GRUB, you need to boot from your windows disc and enter the recovery console where you run
```
fixmbr
```

Once upon a time, I had the same problem, and this didn't work.

So my question is, do you have Windows installed, and you need to get rid of GRUB, or do you have nothing installed?

If you have nothing installed at all, then whatever you end up installing should get rid of GRUB, or use it and reconfigure it.

If you *do* have Windows installed, and you just want to get rid of GRUB and use the Windows boot loader, all of these fixmbr commands and others you will find will probably not work.  They didn't for me a while back.  The only thing I got to work was [the Super Grub disk](http://supergrub.forjamari.linex.org/).  Burn the iso to a CD and boot to that CD.  There is an option to restore the Windows boot loader.  That is the only thing I found that actually overwrites GRUB correctly.

---

### Post by crhis on 2008-03-09
i have no windows installed. My my friend took my copy and never gave it back. I never had one, i just want to wipe my hdd clean. That is all, all i have on it right now(i think) is grub.

---

