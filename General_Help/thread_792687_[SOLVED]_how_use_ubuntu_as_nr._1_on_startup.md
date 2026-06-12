---
title: "[SOLVED] how use ubuntu as nr. 1 on startup"
date: 2008-05-13
forum: General Help
---

### Post by agoraphobia55 on 2008-05-13
hi there!

i am from austria, so i hope u understand my english!

i always have the same problem: i use ubuntu 9 from 10 times, but if i start the computer an leave him on his own, he will start windows because its on first in the row. is it possible to change the positions at the boot up?

thx for help

hp

---

### Post by 505 on 2008-05-13
Yes, in Ubuntu, do 'gksu gedit  /boot/grub/menu.lst' and find the line 'default 0' and change this to 'default 1' (or whatever option you want as default). So the first line is 0, the second 1, etc. If you're unsure, look at the bottom of the file and look for entries with 'title'.

---

### Post by Vadi on 2008-05-13
Or for a more user-friendly and less confusing way, click here to install startup manager: [apt:startupmanager]("apt:startupmanager"), then go to System - Administration - Start-Up Manager, and then select Ubuntu as the default operating system right there. Click Close and you're done!

---

### Post by ago on 2008-05-14
[https://wiki.ubuntu.com/WubiGuide#head-c205c4f58cdcc9bcbdc1bcdb17c1e7ca0eb79756](https://wiki.ubuntu.com/WubiGuide#head-c205c4f58cdcc9bcbdc1bcdb17c1e7ca0eb79756)

---

### Post by Vadi on 2008-05-14
Ohh, right, sorry. Ignore my post.

---

