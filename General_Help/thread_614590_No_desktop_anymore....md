---
title: "No desktop anymore..."
date: 2007-11-16
forum: General Help
---

### Post by Fxy on 2007-11-16
Hi
 
Up till recently ubuntu was working ok in low memory mode, till the other day when i went to boot it up & instead of getting the ubuntu login screen, i got & still get a non graphical login. The login is in terminal or grub or something, i can still login but after login it stays in non graphical mode. Can anyone pls tell me how to get out of this non graphical mode:confused:... Also because im running on a very old and sluggish computer, can anyone also pls tell me how to make the desktop environment run faster. Thats once and if i get it back...

---

### Post by michalski7777 on 2007-11-16
you may have configured something for xserver (the screen manager) that doesnt fit right.

 if so im not sure how to fix that, 

but maybe its just starting into graphical mode just to p*** you off. so when you get to the terminal after booting type:

**sudo telinit 5**

if that doesnt work it should give back an error code

if it works fix it so it starts in graphical mode 
im new so i dont know how to do this :mad:

sorry i cant help you more

---

### Post by bingoUV on 2007-11-16
after login, type startx in the terminal and press enter. Hopefully it will return you to graphical desktop, or at least tell you the reason why it can't do that.

---

### Post by Fxy on 2007-11-19
Thnx michalski7777 & bingoUV for ur help.  Ill try ur posts once i get home, hope they work.  If not ill try fiddlin around & stuff...

---

