---
title: "disable xgl = no awn"
date: 2008-05-07
forum: General Help
---

### Post by Blajano on 2008-05-07
hi everyone. first of all, the forum rocks, it's really helpful for me, an ubuntu beginner haha
Anyways. today i installed Avant Window Navigator, but everytime i want to run Awn, i have to enable the desktop effects (i mean XGL. I had to install the xserver-xgl btw). so when i run Awn, xgl is also running, and my video is just 32mb since is integrated with the motherboard. 

So, is there anyway i can run Awn, without having to enable the desktop effects? to not slow down my computer?

thx

---

### Post by Joeb454 on 2008-05-07
No there isn't sorry :(

AWN Needs a compositor (i.e. Compiz / Desktop Effects) to run :)

---

### Post by twright on 2008-05-07
slimbar is like awn but it doesn't need compiz

---

### Post by FuturePilot on 2008-05-07
If you're using Ubuntu 8.04 you can use Metacity's built in compositor.
To enable it press Alt+F2 and enter
```
gconf-editor
```
Navigate to Apps&#8594;Metacity&#8594;General and check the box that says "compositing_manager"
Make sure you have Compiz disabled for before doing that. Also you don't need XGL for that. It's a very light, simple compositor. It's enough to run stuff like AWN.

---

### Post by Blajano on 2008-05-08
> **FuturePilot said:**
> If you're using Ubuntu 8.04 you can use Metacity's built in compositor.
To enable it press Alt+F2 and enter
```
gconf-editor
```
Navigate to Apps&#8594;Metacity&#8594;General and check the box that says "compositing_manager"
Make sure you have Compiz disabled for before doing that. Also you don't need XGL for that. It's a very light, simple compositor. It's enough to run stuff like AWN.

WOW thanks, that really worked.
I had to uninstall the xserver-xgl btw, i can't really enable the desktop effects, but i can run Awn =D

thanks a lot

---

