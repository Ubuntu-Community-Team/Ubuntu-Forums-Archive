---
title: "grub menu.lst keeps changing?"
date: 2007-06-11
forum: General Help
---

### Post by natedog on 2007-06-11
I installed Ubuntu 7.04 on my in-laws machine. It dual boots with XP. Everything was working great and then a couple days later, the entry for XP got removed from the menu.lst. If I edit the menu.lst file it works for a couple  of days with multiple reboots and then all on its own the XP entry in gone again. Does any one know what it going on?? Thanks!

---

### Post by merlinus on 2007-06-11
Can you post /boot/grub/menu.lst....

Maybe that will offer some insights.

-merlin

---

### Post by veerakumar on 2007-06-11
Novice
just do 
root (hd?)
chainloader +1
boot
in the grub console

---

