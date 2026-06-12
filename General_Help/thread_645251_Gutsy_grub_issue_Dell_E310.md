---
title: "Gutsy grub issue: Dell E310"
date: 2007-12-19
forum: General Help
---

### Post by dakar8 on 2007-12-19
Hey, I've been trying to go through the forums to solve this problem, but I can't find anything.  I have installed gutsy on my parent's dell e310 with xp media edition.  When grub loads, part of the selection box is above the screen and the other half below; not centered.  This obstructs all of the selections.  Can anyone help me get the grub selector in the center of the screen?

---

### Post by erfahren on 2007-12-20
maybe it's a problem with the BIOS not setting a proper basic (usuable) resolution.

or maybe something in GRUB's menu.lst is corrupted (notably the "defoptions" setting):
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```

see this guide: [http://ubuntuforums.org/showthread.php?p=1541970](http://ubuntuforums.org/showthread.php?p=1541970)

could also see if there's an update for the BIOS

---

