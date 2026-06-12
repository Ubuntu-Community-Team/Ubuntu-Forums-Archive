---
title: "boot menue, boot order. whare? what?"
date: 2008-06-03
forum: General Help
---

### Post by Errors suck! &quot;Kairu&quot; on 2008-06-03
hi there, i have dual boot an i want to change my boot order.
right now ubuntu is at the top of the list and starts atomatically, i want this to be for windows. as far as i understand i enter the command 

"gksudo gedit /boot/grub/menue.lst"               (without quotes) 

into the command terminal (after ubuntu boot up), enter my password and it brings up a screen. as what to do next, im clueless.

 please guide me, or say ive done it all wrong and tell me what to do.
                        thanx, kairu

---

### Post by TeoBigusGeekus on 2008-06-03
```
gksudo gedit /boot/grub/menu.lst
```
Post us its contents and we'll tell you what to do.

EDIT:
Forgot to tell you that menu.lst is a file that contains the grub menu specifications - grub is Ubuntu's bootloader.

---

