---
title: "Need to change default boot in grub"
date: 2005-10-04
forum: General Help
---

### Post by kanezfan on 2005-10-04
So the wife and I share this computer and I need Windows XP to be the default choice in GRUB in case there's a power outage or something.  I did this in Gentoo, but now I can't remember how to edit the file in /boot/grub/.

---

### Post by nike984 on 2005-10-04
[QUOTE=kanezfan]So the wife and I share this computer and I need Windows XP to be the default choice in GRUB in case there's a power outage or something.  I did this in Gentoo, but now I can't remember how to edit the file in /boot/grub/.[/QUOTE]

in a terminal, type 
```
sudo gedit /boot/grub/menu.lst
```

change the default 0 to default #(Number of WinXP)
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 0

```

Usually WinXP is 4

God luck~\\\\:D/

---

