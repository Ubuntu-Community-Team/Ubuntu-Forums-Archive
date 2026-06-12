---
title: "mouse (touchpad) working, but pointer not visible"
date: 2016-05-01
forum: General Help
---

### Post by roberto32 on 2016-05-01
after login it often happens that mouse cursor (pointer) is not visible. I only know where's the mouse is when there's smth like "onmouseover" or "onfocus"... on webpage. This thing happened after upgrade to 16.04. So I've to do ```
 service lightdm restart 
``` but that of course restarts my session and I've to save all work in vim or atom editors.... Isn't it possible only to restart mouse somehow ?

---

### Post by roberto32 on 2016-05-01
may it be graphics related? I've Nvidia Gforce 720M  and I'm using the opensource driver, should I use the proprietary one form Nvidia?

---

### Post by PaulW2U on 2016-05-01
> **roberto32 said:**
> after login it often happens that mouse cursor (pointer) is not visible. I only know where's the mouse is when there's smth like "onmouseover" or "onfocus"... on webpage. This thing happened after upgrade to 16.04.
I would have said it was this bug - [Mouse cursor lost when unlocking with Intel graphics]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604") - which seems to be affecting just Xubuntu and Lubuntu but you say that you don't have Intel graphics.

May be a better workaround might be to move to a vt and back again with **Ctrl+Alt+F1** and then **Ctrl+Alt+F7**. Does that bring the mouse pointer back?

Hope that helps.

---

### Post by roberto32 on 2016-05-01
thanks it helps, I was trying ctrl+alt+f2 instead of f1, btw I can't find anywhere what those f(x) means. I only know f2 is terminal and f7 is X running

---

### Post by Impavidus on 2016-05-02
F1 to F6 all give you a terminal. There are 6 of them. F7 is the graphical one. It doesn't matter which of F1-F6 you use.

---

### Post by sven-glueckspilz on 2016-06-17
Good man! Thanks a lot for this!

---

