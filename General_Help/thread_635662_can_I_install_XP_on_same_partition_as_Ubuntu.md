---
title: "can I install XP on same partition as Ubuntu?"
date: 2007-12-09
forum: General Help
---

### Post by Steve05TSX on 2007-12-09
without having to format!!  I spent hours and hours setting this thing up.  I don't wanna go through that process again!! one downfall is that the linux is 64bit and xp is 32

---

### Post by UK-Wobbie on 2007-12-09
> **Steve05TSX said:**
> without having to format!!  I spent hours and hours setting this thing up.  I don't wanna go through that process again!! one downfall is that the linux is 64bit and xp is 32

Get your self VirtualBox.
You can run Xp,Ubuntu,Vister Anything in it!

[http://www.virtualbox.org/](http://www.virtualbox.org/)

The bestway out of F**king things up :lolflag: Virtuabox..:guitar:

Rob :)

---

### Post by Lostincyberspace on 2007-12-09
No you can format to the ntfs file system with gparted or parted magic it is a "little" faster (ie 99:100).

:lol:

P.S. there is 64bit XP

---

### Post by CatKiller on 2007-12-09
> **Steve05TSX said:**
> without having to format!!  I spent hours and hours setting this thing up.  I don't wanna go through that process again!! one downfall is that the linux is 64bit and xp is 32

You can't install XP on the same partition without using some kind of virtualisation software, but you can install it on the same hard drive. They aren't quite the same thing. See, for example, [here]("http://en.wikipedia.org/wiki/Disk_partitioning")

You'll need to use GParted, either from the Ubuntu live cd or the GParted live cd, to make your existing partitions smaller and create a new Primary partition for Windows. Then install Windows, and then you'll need to re-install GRUB because Windows will install its own bootloader into the Master Boot Record. Have a search on "Re-installing GRUB after installing Windows" - there's a howto somewhere, but I can't remember where I saw it.

---

### Post by Lostincyberspace on 2007-12-09
You can just burn the Grub boot disk and revert to grub from there. You then need to add xp to your to grub list file but its not very hard.

---

