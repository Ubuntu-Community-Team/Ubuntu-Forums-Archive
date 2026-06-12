---
title: "This is an insane problem and it shows my stupidity...."
date: 2008-06-14
forum: General Help
---

### Post by wookietim on 2008-06-14
Okay, I wanted a simple way to load random images from Flickr as wallpaper. So I ended up installing "SuperKaramba" on my system because it had something called a "Wallpaper changer" as one of it's widgets... I don't particularly like it since it doesn't do what I want it to do...

But, for some reason, I added it to my KDE4 taskbar. I have tried uninstalling it from superkaramba. I can't right click on the panel to remove it (It only offers a menu that says "Update5" when I try right clicking on it) and it takes up half the taskbar. I want it out of my taskbar and I can't get it to go away!!!

How do I get rid of it?

---

### Post by LeoSolaris on 2008-06-14
Pull up terminal type in ```
top
```

That will give you a list of everything running. (you did uninstall superkaramba through something like synaptic or add/remove right?) Look through that list till you find one of them related to the program. open a second terminal and type ```
sudo killall {the name of the program}
``` You can skip straight to the killall part and try superkaramba as the name, and it may be right.

It may just be that it is running in memory still if you have not restarted since removal. It's a renavant at that point. It's dead and removed, it just doesn't know it yet.

---

### Post by wookietim on 2008-06-14
Actually, I originally thought in the same direction - uninstalled Karamba and did a cold restart of the machine - still there (With 6 useless slots for wallpaper - maybe)....

---

### Post by wookietim on 2008-06-14
Arghhhhh!!!!!

Okay - I finally got the widget to go away. But now, on startup, in it's place is the phrase "This Object Could Not Be Created.", which is even more annoying than the widget....

Please - I'm willing to wade into config files if I have to - someone just point me in the right direction!

---

### Post by wookietim on 2008-06-14
Solved! In case anyone else has this type of a problem :

The config file for KDE 4 is in .kde/share/config/

Poking around in the file you will find the applets that run in there. All you have to do is delete the two blocks that mention that applet, logout and login and it will be gone.

---

