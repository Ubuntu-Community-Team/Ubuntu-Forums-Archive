---
title: "Kubuntu crashes on startup"
date: 2007-06-18
forum: General Help
---

### Post by Game_boy on 2007-06-18
When I turn on my computer and select Kubuntu from the bootloader, it shows the loading bar, that fills up, the screen flickers to a long terminal message which says something like "...will resume...", then it flickers to an empty loading bar, then a completely black screen, then a very dark grey screen, then freezes. The only way to end it is by pushing the power button which shows the usual backwards loading bar.

Is it recoverable without losing all my files?

---

### Post by kuja on 2007-06-19
I would try booting without usplash to see if that helped

When you're in the boot loader select the line for kubuntu and press 'e' (edit), drop down to the line that starts with kernel and press 'e' again, remove splash from the line and press enter, then press 'b' to boot.

---

