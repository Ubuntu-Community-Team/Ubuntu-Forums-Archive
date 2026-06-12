---
title: "XP won't accept hard drive"
date: 2007-12-23
forum: General Help
---

### Post by energie91 on 2007-12-23
I kind of have a problem.

Whenever I try to install XP on my second hard drive, XP tells me it is not under a correct format and tells me to delete the partition and create a proper one. Well, even if I do that it just won't work.

I tried reformatting my drive with sudo gparted but I still have the same problem, I tried wiping my drive with the ultimate boot cd but it also failed (Im not quite sure everything was right thought but Ill retry if needed). I also tried the gparted live cd but that doesn't work either, still give me the same error.

Oh and I tried with 2 different xp cds by the way. Now if someone could help me out I'd really appreciate it.

Second question is, if I install XP on my slave drive (the one Im trying to fix), will Grub understand or will I need to boot into Ubuntu and fix my menu.lst accordingly ?

Thanks you for your kind help :).

---

### Post by Craigus on 2007-12-23
XP wants to be on the primary drive. You can install it on a slave drive, but you need to set the slave drive as the first boot drive in bios to do it. The way I do it is to actually make the drive the primary drive in the computer, install XP, and then make it the slave drive. You'll have to do this in grub to be able to boot then:

> title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by energie91 on 2007-12-23
Wow, Ill go try that. I feel dumb.

---

