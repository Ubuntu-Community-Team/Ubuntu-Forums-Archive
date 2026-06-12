---
title: "how to edit menu.lst to include fedora core 6"
date: 2007-01-04
forum: General Help
---

### Post by sdowney717 on 2007-01-04
I want to edit menu.lst to include booting for fedora core 6
when I type uname -r in fedora I get
2.6.18-1.2798.fe6

What do I do?
thanks

---

### Post by bodhi.zazen on 2007-01-04
Mount your Ubuntu partition in Fedora.

Open Fedora /boot/grub/menu/lst

Copy/paste the fedora entry to Ubuntu /boot/grub/menu/lst

Save and exit your editors

---

