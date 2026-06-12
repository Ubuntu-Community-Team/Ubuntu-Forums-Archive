---
title: "Dual Display [laptop display / vga to monitor]"
date: 2006-11-07
forum: General Help
---

### Post by robgill on 2006-11-07
In Windows I can easily extend my desktop to an 2nd display by right clicking the desktop and changing display output to extend desktop to monitor.  

(then I can have my desktop with start menu on my laptop display drag windows and programs to the other monitor - it's really the only thing I miss from windows)

When I plug the external monitor into the vga-out port in ubuntu(gnome), I get an off center duplication of my desktop.

I searched the forums and nearly all of the dual monitor posts used two video cards or ati/nvidea cards.  I have a VAIO FS640 and would like to use the laptop display and vga-out.  It has an Intel Mobile 915GM/GMS/910GML Express Graphics Controller.  Let me know if any more info is needed

Any idea how I can duplicate that part of my windows experience? I know it's capable of doing, but I don't know if I can do it in Ubuntu.

Thanks, I appreciate any help

---

### Post by johnnymac on 2006-11-08
Easy enough...this can be accomplished using Xinerama

This should get you going...

[http://www.ubuntuforums.org/showthread.php?t=221174&highlight=Xinerama](http://www.ubuntuforums.org/showthread.php?t=221174&highlight=Xinerama)

---

### Post by robgill on 2006-11-08
Thanks, I'll try that tomorow assuming that guide works for dapper and xinerama won't cause slowdown?

---

### Post by vidak on 2006-11-08
> **robgill said:**
> Thanks, I'll try that tomorow assuming that guide works for dapper and xinerama won't cause slowdown?

I use an Acer laptop with the same (Intel 915GM) graphic card, and I didn't find xinerama too slow. 6 desktops with 2 VNC-windows, firefox and java applets runs quite fine.

---

### Post by robgill on 2006-11-08
After reading through the guide several times and examining my xorg.conf file, I think I won't have any problem setting this up.

My concern now is that I won't always use the dual display (since I take my laptop with me) and when I disconnect the second display, X will still think I am on dual display.  Will this cause any problems?

---

### Post by insub2 on 2006-11-12
i would like to know that same thing.  what happens when you unplug the external monitor when using Xinerama?

---

### Post by insub2 on 2006-11-15
> **robgill said:**
> My concern now is that I won't always use the dual display (since I take my laptop with me) and when I disconnect the second display, X will still think I am on dual display.  Will this cause any problems?


I found the answer...
[http://en.wikipedia.org/wiki/Xinerama]("http://en.wikipedia.org/wiki/Xinerama")

unfortunately the answer is yes, it will still think there is a screen there.  the only problems are your mouse can disappear off screen (actually on the other screen that isn't plugged in) and because it is still sending video, it will use power.

---

### Post by elektronaut on 2007-01-10
You can have two ServerLayout sections, one for single screen, and one for dual screen, and then switch them without rebooting. There are some threads about this, bodhi.zazen has written some good HowTos.

---

