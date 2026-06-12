---
title: "Dual boot on Sata and IDE?"
date: 2007-04-25
forum: General Help
---

### Post by teejeaux on 2007-04-25
Ok, I've looked all over the web, tried a multitude of different things. I've created a GRUB BIN file for Vista, I've edited the menu.lst file in Feisty, and I still have the same problem.  I can't get either menu to boot the other OS properly.  This is my setup:

Vista on SATA1
Feisty on IDE1

Both boot properly if I set to boot from that drive in the bios.  So if I set the bios to boot from SATA1, Vista boots just fine, but the GRUB entry I've created using all the instructions, won't boot Ubuntu.

If I set the bios to boot from IDE1, then GRUB comes up, and I can boot UBUNTU fine. But if I select the Vista option, I get BOOTMGR not found.  I've tried the "rootnoverify" option, and I've changed the hard disk locations, but still no joy in Mudville.

Does anyone have any other suggestions I might try?

Thanks!
Teejeaux

---

