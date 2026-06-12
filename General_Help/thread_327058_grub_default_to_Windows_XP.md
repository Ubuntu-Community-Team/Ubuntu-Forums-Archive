---
title: "grub default to Windows XP"
date: 2006-12-28
forum: General Help
---

### Post by heneghan on 2006-12-28
How do I get grub to default to windows XP on power up?  I am hesitant to just try things in menu.lst since I may get a non bootable system.
Thanks, Mike

---

### Post by usien on 2006-12-28
i think u will eventually hav 2 play with menu.lst so go ahead nd do it.there r instructions in menu.lst on how 2 change the default.u just hav 2 change the no. of the 'default' option 2 point to the windows entry no. in the list.

---

### Post by bulldog on 2006-12-28
> **heneghan said:**
> How do I get grub to default to windows XP on power up?  I am hesitant to just try things in menu.lst since I may get a non bootable system.
Thanks, Mike

Count the entry's for kernels and memtest in menu.lst and change this to what number is windows,```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0  **change this zero in whatever your windows entry is**
```

---

