---
title: "Lilo and Grub"
date: 2006-07-29
forum: General Help
---

### Post by geovino on 2006-07-29
I have Win XP on the hda (80gb) and PCLinuxOS on hdb (40gb). I want to partition the hda drive and give Ubuntu 40gb. PCLinuxOS uses Lilo, how can I add Ubuntu to that Lilo bootloader or can I use GRUB to bootload all three?

Thank you

---

### Post by scxtt on 2006-07-30
when installing ubuntu, grub should 'find' the other 2 OSes and add them to /boot/grub/menu.lst ...

---

