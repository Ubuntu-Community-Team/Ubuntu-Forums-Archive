---
title: "Recent Kernel Update hid Windows XP in GRUB"
date: 2006-08-08
forum: General Help
---

### Post by Patrick-Ruff on 2006-08-08
hey all something odd happend after I updated my entire ubuntu machine, I updated the kernel as well and it of course showed up in the GRUB boot menu as well as the older kernel, but it seems to have removed my Windows XP Home partition from the list, how can I possibly put it back in there? I can't remember what the exact code to type in and such.


thanks

---

### Post by Ramses de Norre on 2006-08-08
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Windows XP Media Center Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

Change the root to the appropriate partition.

---

### Post by Tomosaur on 2006-08-08
Hide the older kernels, mayhaps?

---

### Post by Patrick-Ruff on 2006-08-08
I tried that trust me, thanks anyways Tomosaur, it was removed from the menu.lst file, thank you Ramses.

---

### Post by mchatel on 2006-08-08
Did the kernel update (and corresponding GRUB menu update) actually remove the Windows XP item entirely, or did it just shove the entry further down the list, onto a 2nd page of entries?  That could happen, if you have a lot of kernel updates listed in your GRUB menu.  I usually remove all of them, and only keep the most recent 2 kernel entries.

---

### Post by Tomosaur on 2006-08-08
I keep my kernels, but I limit my Grub menu to just 1. I've never had a recovery console fail on me yet, so I should be ok :P

---

