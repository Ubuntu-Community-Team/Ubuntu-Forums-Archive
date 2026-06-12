---
title: "HELP: Editing GRUB"
date: 2007-05-05
forum: General Help
---

### Post by zuner on 2007-05-05
I would like to change my default OS to XP and I want to hide memtest86 and the ubuntu recovery mode choices. What do I do?

---

### Post by Thingymebob on 2007-05-05
comment the items out in /boot/grub/menu.lst

eg:```
title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1837b293-14ff-4ed9-bcb1-d0206521ff30 ro single vga=792
initrd          /boot/initr{d.img-2.6.20-15-generic
```
would read:
```
#title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.20-15-generic #root=UUID=1837b293-14ff-4ed9-bcb1-d0206521ff30 ro single vga=792
#initrd          /boot/initrd.img-2.6.20-15-generic

```

or you could hide the menu by uncommenting the hiddenmenu line (Make sure your default is set correctly) - 0 being the first option in the list

---

### Post by zuner on 2007-05-05
Would I edit this in GRUB, or another program. If so, how?

---

### Post by jfinkels on 2007-05-05
> **zuner said:**
> Would I edit this in GRUB, or another program. If so, how?

First you should always make a backup copy of /boot/grub/menu.lst:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```

To edit this file, open your favorite text editor as root:
```

gksudo gedit /boot/grub/menu.lst

```

Then save it and you should be hunky dorey (sp?), as they say.

---

### Post by Thingymebob on 2007-05-05
do it in gedit
in a terminal type **sudo gedit /boot/grub/menu.lst**

---

### Post by zuner on 2007-05-05
OK. I still don't understand how to change XP to default. Can you be a liitle more specific?

---

### Post by Thingymebob on 2007-05-05
in menu.lst change the value of default to the position winxp appears in the list. Its right at the top
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default         0**
```
numbering starts at 0 so if winxp appears as the 3rd item in your menu then set this to 2

---

