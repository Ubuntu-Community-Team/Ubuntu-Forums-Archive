---
title: "ccsm doesn't remember settings (in hardy)"
date: 2008-05-03
forum: General Help
---

### Post by jeremz on 2008-05-03
So, it seems to me that in Hardy, there is no way to turn your visual effects off, then turn them back on again and have ccsm remember the settings. Am I mistaken? I have played with various combinations of having ccsm and simple ccsm installed to no avail. I can change settings around, but they just don't stick. Any thoughts anyone has would be greatly appreciated. Am I missing something silly?

---

### Post by macaholic on 2008-05-03
Why are you turning them on and off that much? If you need to stop compiz for whatever reason, just run metacity --replace, it is unnecessary to disable visual effects altogether.

---

### Post by tommyhakinen on 2008-05-03
to easily turn on/off compiz fusion, you can use the compiz fusion icon. to install it just type this on terminal and enter your password when prompted:

> 
sudo apt-get install fusion-icon


then go to System Tools > Compiz Fusion Icon, the compiz Fusion Icon will be shown on the notification area. To switch between Normal setting(metacity) and compiz, just right click on the fusion icon and select accordingly under Window Manager.

---

### Post by jeremz on 2008-05-16
I think you guys are missing my point, perhaps I didn't make myself clear. I'm not trying to find ways to turn compiz off and on, nor am I doing it that often. However, once in a great while, compiz has been known to crash on me while running previous versions of Ubuntu. After installing Hardy, something was wrong there for a while, where whenever I started my system up, or compiz would get shut off for what ever reason, it did not remember my settings when fired back up. I tried exporting profiles and importing them again, and it wasn't having any effect. Somehow the problem has fixed itself. I'm curious to know if anyone else has had this experience.

---

