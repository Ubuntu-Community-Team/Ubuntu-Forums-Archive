---
title: "Kubuntu Gusty Worked fine off the dvd, but now it is just &quot;screwed&quot;?"
date: 2007-10-02
forum: General Help
---

### Post by notna01 on 2007-10-02
Kubuntu Gusty Worked fine off the dvd, but now it is just "screwed"?
Ok, when I used the DVD to install kubuntu gusty (loosing all of my old data) it seemed to be running nicely.
But when it boots up off the hard drive, all I get are wierd avacado green lines and white. (and a bit of blue) It has no fonts, now pics, no nothing. I thought ubuntu was bad when I screwed up the panels, but kubuntu already screwed when I install it?
(Oh, and ctrl+alt+f1's terminal works fine. it's just the x-server that aint working right)
So, what do I do? 
-Reinstall
-Install Ubuntu
-Uninstall and give disk space back to vista

---

### Post by notna01 on 2007-10-02
I dont mean to double post, but I need urgant help!

---

### Post by shad0w_walker on 2007-10-02
It sounds like the graphics driver is screwed up for your Xserver. Switching to the vesa driver might help until you can get the proper drivers installed.

---

### Post by strabes on 2007-10-02
Run this command in the Ctrl+Alt+F1 terminal (aka framebuffer):```
sudo dpkg-reconfigure xserver-xorg
```

Accept all the defaults & use the vesa video driver. Then you can run ```
sudo reboot
```Your X server should start up well now.

PS. Threatening us with reinstalling vista isn't going to make us want to help you more.

---

### Post by notna01 on 2007-10-03
> **strabes said:**
> Run this command in the Ctrl+Alt+F1 terminal (aka framebuffer):```
sudo dpkg-reconfigure xserver-xorg
```

Accept all the defaults & use the vesa video driver. Then you can run ```
sudo reboot
```Your X server should start up well now.

PS. Threatening us with reinstalling vista isn't going to make us want to help you more.

Vista was already installed... I was just wondering if I should dump ubuntu and give the mem back to vista....

---

### Post by notna01 on 2007-10-03
CRAP, now its even worse :(
Now its only terminal....
So far, I've installed it twice.... The only thing I have learned today is that Windows Uses almost the same thing as KDE, because when I booted into kubuntu after using vista, instead of lines, it was showing vista's desktop

---

### Post by notna01 on 2007-10-03
Oh, com'on guys, I need help here...

---

