---
title: "help! grub is not working"
date: 2007-05-24
forum: General Help
---

### Post by zazeem on 2007-05-24
hi all, recently my computer was acting funky so i went in and swapped my hard drives around to a different ide setup, i set it to the correct one in my bios but my ubuntu still does not boot it says insert system disk to continue, so for the hell of it i put a winxp cd in and all of a sudden i didnt hit any key and next thing i knew grub starting booting my ubuntu up, its the weirdest thing!! when i take the xp cd out it does not boot anymore how do i fix this so ubuntu loads without my xp cd? it used to work fine

---

### Post by vtel57 on 2007-05-24
Well, the problem here is that when you swapped your drives around, you confused GRUB. Your system needs to boot to whichever drive had GRUB on the Master Boot Record (usually the one you installed Ubuntu on). Also, now all the GRUB menu entries are incorrect because the drives are not in their previous physical address locations. You'll need to manually edit /boot/grub/menu.lst to reflect your hardware changes.

---

