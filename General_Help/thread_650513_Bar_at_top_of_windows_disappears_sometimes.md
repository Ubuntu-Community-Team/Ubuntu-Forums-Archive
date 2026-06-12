---
title: "Bar at top of windows disappears sometimes"
date: 2007-12-26
forum: General Help
---

### Post by artinla on 2007-12-26
I have the Ultimate Edition 2007, which is gutsy with a gussied up gnome desktop and a bunch more preinstalled apps.  This is a clean install with only the following added afterward:

Google Earth, Frostwire, Amule, ConvertIT, Flashplugin-nonfree, Stellarium.

I enabled the 3D Nvidia driver and it is working fine.  Compiz and Beryl are installed and working.  I have the desktop cube, rotate desktop and wobbly windows enabled.  Gdesklets are installed and working.  I have a few desklets on the desktop.

I then did all the current updates from the Ubuntu Update Manager.  I disabled any custom repo's first.

When I rebooted, it defaulted to the Kubuntu Desktop, but I was able to switch my session back to the Gnome one.  Everything seemed fine, but now I notice that when I open some of the applications (Frostwire and Kopete are the worst offenders) the bar at the top (where you can minimize, maximize, exit, etc) goes away and you can't close the program any more.  Xkill will get rid of it, but after a minute or two everything starts locking up and I have to reboot to get things working again.  

Kopete is the worst, Frostwire comes up with a blank white box, and neither one works.  They lose the top bar almost immediately.  There are others that do it, but I can't remember them all right now.  I think that the problem started when I did the ubuntu updates yesterday.

Almost all my normal apps work, but even they lose the top bar if I open one of the bad apps while they are active.  Even the terminal window is affected.

Restarting X doesn't help, because each time I restart it after the weirdness starts things get worse and worse.  A reboot is the only way to straighten things out.  All is fine unless I start one of the "Bad Apps"  Thing is, I can't put my finger on what the common denominator is between all the apps that lock up.

Can anyone suggest a good way to isolate the problem?  I am at a loss on where to start.

Thanks,

Art

---

### Post by TidusBlade on 2007-12-26
When the windows start dissapearing try pressing ALT+F2 and typing "metacity --replace" if possible.

---

### Post by artinla on 2007-12-26
I will try that.  Is metacity the component that produces my disappearing bar?  What is that bar called anyway?

Thanks,

Art

---

### Post by t3hi3x on 2007-12-27
It depends. If you are using compiz's bar then its emerald. I guess since compiz is still its early stages it has some issues. I have never had a problem with metacity crashing (thats the standard gnome bar).

I made a little shortcut on my panel that just runs emerald --replace when it disappears. (It does it a lot less than it did with feisty)

---

### Post by Znort_Ubern00b on 2007-12-27
sudo nvidia-xconfig --add-argb-glx-visuals -d 24


type that into terminal it should clear the problem.

---

