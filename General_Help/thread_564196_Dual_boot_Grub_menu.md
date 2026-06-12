---
title: "Dual boot Grub menu"
date: 2007-09-30
forum: General Help
---

### Post by planC on 2007-09-30
Could someone help me with the code to change the default operating system boot up for grub menu. I tried 'sudo cp /boot/grub.menu.1st /boot/grub/menu.1st_backup' as per the feisty command notes, but no go. The 'board of control' wants windows to start up first. Cheers:)

---

### Post by chuckyp on 2007-09-30
The comand above would just backup a copy of your grub configuration file.  You still need to manually edit it.
```

sudo nano /boot/grub/menu.1st

```
Change the default boot option from 0 to which ever os you want.  Remember the count starts at 0 and goes up for each entry ex: 0,1,2  etc....

---

### Post by planC on 2007-09-30
I put that in and got a shell konsole, but don't know how that works and it wouldn't open a help file. What happens in the shell and how do I get the "^G" etc to work?:)

---

### Post by logos34 on 2007-10-01
use 

gksudo gedit /boot/grub/menu.lst

---

### Post by MarkieB on 2007-10-01
I'm relatively sure it's menu.lst not menu.1st ?

---

### Post by Zalbor on 2007-10-01
Yes, it's menu.lst. With an L.

A safer way to do it would be to change the number to "default" (no quotes) and add a line that says "savedefault" (no quotes) under the Windows entry (I think just below the line beginning with "root"). Also remove "savedefault" from anywhere else that it appears.
EDIT: Actually I'm not sure the correct word is "default".

---

