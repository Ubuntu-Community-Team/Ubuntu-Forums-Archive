---
title: "Booting problems"
date: 2007-05-23
forum: General Help
---

### Post by blueangel1953 on 2007-05-23
I had XP installed before I installed Ubuntu, now when I go to turn on my pc I am presented with Grub Bootloader which if I don't do anything it automatically boots into Ubuntu. Now I only use Ubuntu to mess around with so I prefer to boot in XP as default. Is there anyway to edit Grub to boot XP by default?

---

### Post by cantormath on 2007-05-23
> **blueangel1953 said:**
> I had XP installed before I installed Ubuntu, now when I go to turn on my pc I am presented with Grub Bootloader which if I don't do anything it automatically boots into Ubuntu. Now I only use Ubuntu to mess around with so I prefer to boot in XP as default. Is there anyway to edit Grub to boot XP by default?

Yes you can.
open menu.lst and change default to whatever number windows is on the grub list.
```
 :~$ sudo gedit /boot/grub/menu.lst 
``` 

you will see
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0 
change default at the end from 0 to whatever number the windows install is on the grub list.
Save and reboot. Hope that helps.

---

