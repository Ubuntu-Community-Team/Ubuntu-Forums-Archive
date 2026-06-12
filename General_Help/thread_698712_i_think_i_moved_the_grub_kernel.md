---
title: "i think i moved the grub kernel"
date: 2008-02-16
forum: General Help
---

### Post by twoprophets on 2008-02-16
so i was trying to move the grub kernel to my windows partition so i could remove ubuntu
when i get to the boot menu, i went to the edit section and it displays it as hd0,0
but when i go through the command line part and put in find /boot/grub/stage1, it states it as being under hd1,0
i have 3 windows xp discs and they are all copies of the orginals which i dont have

---

### Post by 444 on 2008-02-16
That's not how you remove Ubuntu.

Boot up any of the XP discs, go to the Recovery Console, and run fixmbr.

---

