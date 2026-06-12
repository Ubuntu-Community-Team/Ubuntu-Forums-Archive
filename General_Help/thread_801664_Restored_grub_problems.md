---
title: "Restored grub problems"
date: 2008-05-20
forum: General Help
---

### Post by TheCl@ssic on 2008-05-20
I re-installed windows and then used super grub to restore grub. The menu doesn't match my previous menu, Windows doesn't boot, and linux has problems. I used the rescue mode option to boot into windows and use a terminal to look at my menu.lst and possibly fix it using backed up versions of it, however the menu.lst (/boot/grub/menu.lst) looks like it did before all of this and isn't what is being used by grub. I'm guessing grub is using a different location for "/boot" but I don't know how to fix it, can anybody help?

---

### Post by TheCl@ssic on 2008-05-20
NM, I got it, although I am curious where super grub put grub and a menu.lst

I used these instructions, [GRUB solution (on its own)]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub#GRUB_solution_.28on_its_own.29"), to fix it. I also had to change the partition number for Windows, probably a result of moving partitions around in Linux since first installing Windows.

---

