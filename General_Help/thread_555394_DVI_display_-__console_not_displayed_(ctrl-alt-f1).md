---
title: "DVI display -  console not displayed (ctrl-alt-f1)"
date: 2007-09-20
forum: General Help
---

### Post by Lem on 2007-09-20
I'm using a Formac Gallery monitor on a board with the Intel 945GM chipset. This monitor only has DVI. I set up Ubuntu using a VGA monitor (BIOS won't display on the DVI!) and it works fine now using the DVI monitor.

However - If I want to go into a text console (ie. ctrl-alt-f1), the screen goes blank (fine under VGA). I'm not getting the bios/post messages displayed either, so I don't know if this is related.
It seems that I might have to change the mode the text console is displayed in, but I'm sure how to do this.

---

### Post by Lem on 2007-09-20
Think I may have worked out a fix by changing the vga option passed to the kernel by grub in menu.lst to a resolution the panel prefers.

---

