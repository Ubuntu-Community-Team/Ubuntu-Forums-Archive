---
title: "GRUB: Will it find my new OS?"
date: 2008-04-01
forum: General Help
---

### Post by Barabbas on 2008-04-01
Hey there, I'm about to format a partition being used by a buggy XP, and clean installing another copy of  XP there. My question is will GRUB find the new OS that was used in the previous bootloader?

---

### Post by lswest on 2008-04-01
Well if you're installing it onto the same drive, XP will overwrite GRUB with it's own bootloader.  To repair GRUB, check the how-to in my signature (second line)

---

### Post by Barabbas on 2008-04-01
Aah, so once GRUB is intact, Ubuntu and XP, will be able to use in the bootloader?

---

### Post by forrestcupp on 2008-04-01
> **Barabbas said:**
> Aah, so once GRUB is intact, Ubuntu and XP, will be able to use in the bootloader?

Yes, they should.  

If it happens to not pick up your XP, you can come back and post your menu.lst and some other commands and we'll work it out.

---

### Post by Barabbas on 2008-04-02
Hey, quick question before i do this, but i how do identify my ubuntu and current xp(one i'm replacing) partition when i set up the new XP?

---

