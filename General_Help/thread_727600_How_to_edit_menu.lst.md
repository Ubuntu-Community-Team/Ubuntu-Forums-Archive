---
title: "How to edit menu.lst??"
date: 2008-03-17
forum: General Help
---

### Post by BETELGEUSE58 on 2008-03-17
Fairly new to linux.

I just want to edit menu.lst (grub) so I can rearrange it.
Ive tried in terminal     sudo gedit boot/grub/menu.lst   
It just takes me to a blank document.
When I double click the file to open it, all the data is there, but not when i try the above command. I cant edit it by opening it by double clicking because I'm not logged in as root.

How do I do this?
Thankyou.

---

### Post by jken146 on 2008-03-17
You got the path wrong.  It is /boot/grub/menu.lst

---

### Post by BETELGEUSE58 on 2008-03-17
KK thx. Thought it was something simple.

---

### Post by oldos2er on 2008-03-17
You should use gksudo for graphical programs, instead of sudo.

---

