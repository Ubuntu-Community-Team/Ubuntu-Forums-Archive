---
title: "Reconfigure graphics - new monitor"
date: 2014-08-27
forum: General Help
---

### Post by timgood on 2014-08-27
I installed Ubuntu 14.04 64bit on a friends old Dell desktop computer. I had it attached to an old 4:3 monitor. Now I have it attached to his widescreen 16:9 monitor, I can't seem to change the resolution. How do I reconfigure the graphics under 14.04? The old methods don't seem to work anymore.

---

### Post by fantab on 2014-08-27
What kind of graphics does that dell have?

Have you tried:
```
rm ~/.config/monitors.xml
```

and restarting ubuntu if need be?

---

### Post by timgood on 2014-08-27
Yes, but no file called monitors.xml in .config

---

### Post by papibe on 2014-08-27
Hi timgood.

Could you open a terminal, run these commands and post back the results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga

ls /etc/X11/xorg.conf

xrandr -q

xrandr -q --q1
```
Regards.

---

### Post by timgood on 2014-08-28
I will do this today. Thanks. There is no /etc/X11/xorg.conf but I will post the output of the other commands.

---

### Post by grahammechanical on 2014-08-28
There is a Displays utility that we can use to detect displays and if we are using a proprietary video driver it will have its own management utility that might allow displays to be detected.

Is this a digital monitor? Modern monitors contain information in their electronics about the capabilities of the device. It is called the Extended Display Identification Data (EDID). Ubuntu reads that data every time it boots. That is why ubuntu does not use an xorg.conf any more.

What cable are you using to connect to that monitor. I recently purchased a digital TV to use as a monitor. The only cable I had available was a VGA cable. VGA is standard on monitors and graphic cards. But I could not get the full range of resolutions that the handbook said the TV was capable of. I brought a HDMI cable and used that and now Ubuntu runs the monitor at the full 1920 x 1080 @ 60 Hz instead of the 1350 x 768 @ 60 Hz that the VGA cable was giving me.

Regards.

---

