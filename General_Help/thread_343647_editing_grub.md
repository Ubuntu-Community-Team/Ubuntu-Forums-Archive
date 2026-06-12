---
title: "editing grub"
date: 2007-01-21
forum: General Help
---

### Post by billybag on 2007-01-21
i have a couple questions involving the grub screen at the beginning of my computers boot-up process. i have updated my linux a few times (hoary to breezy to edgy) so i have a few startup options that i dont need. I can start up using 6.10, breezy, hoary [cant remember the release numbers at the top of my head], or windows. i still use windows on occasion and of course i use edgy... but i never feel the need to startup using previous ubuntu releases. How can i edit this?

also... upon trying to find my answer for the above, i have come across possibly displaying a Splash Image for GRUB menu on boot-up... what is this exactly?

---

### Post by taurus on 2007-01-21
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

