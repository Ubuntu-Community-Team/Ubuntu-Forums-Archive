---
title: "gfxboot"
date: 2007-06-05
forum: General Help
---

### Post by ramboza on 2007-06-05
I've messed up playing with gfxboot...:(
It was all going well, and all the grub menu.lst entries booted correctly, but when i've changed to the new gfxboot theme - the menu item "Windows" stopped booting. It is funny, because it doesn't give any error - the screen blinks for a second - and i see the grub menu again with renewed timer going down...However, i am able to boot in ubuntu. 

I tried to roll back to previous gfxboot theme - no luck same thing.
I tried to reinstall gfxboot package and "grub-install" - no luck.

I've removed gfxmenu from menu.lst and that's what the original grub says when chosing "Windows"

root (hd0,0)
Filesystem unknown partition type 0x7
chainloader +1
makeactive

Grub Loading Stage2...

And that's it - after a second again the grub menu with timer going...

---

### Post by ramboza on 2007-06-05
That's funny, but i've done fixmbr and fixboot from windows recovery console (XP CD) and that worked...i thought that it would erase the grub, but it had not :-)

---

