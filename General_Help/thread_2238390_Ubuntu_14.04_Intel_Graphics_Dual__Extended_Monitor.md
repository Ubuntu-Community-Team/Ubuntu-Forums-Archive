---
title: "Ubuntu 14.04 Intel Graphics Dual / Extended Monitors"
date: 2014-08-07
forum: General Help
---

### Post by josullivan.c on 2014-08-07
Hi all,

Once Ubuntu user returned after a few years messing around with other distros. I have just installed 14.04 and I'm having an issue with my dual monitors. I've Googled this issue only to find solutions for setups with dedicated graphics (Nvidia/ATI) cards. 

My laptop is using integrated Intel graphics. I have two monitors attached to my docking station, but Display is not detecting the seperate screens, and they are just being mirrored. 

Any ideas? I'd like to run an extended desktop over dual monitors (as one does).

Thanks in advance.

---

### Post by papibe on 2014-08-07
Hi josullivan.c. Welcome ):P

Could you open a terminal, run these commands, and post back its results (you can copy/paste the text)?
```
xrandr -q

xrandr -q --q1
```
Regards.

---

### Post by josullivan.c on 2014-08-07
Thanks for reply. As requested:

xrandr -q

```

Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 32767 x 32767
eDP1 connected (normal left inverted right x axis y axis)
   1366x768       60.1 +   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   3840x1200      60.0  
   2560x1024      60.0  
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

xrandr -q --q1

```

SZ:    Pixels          Physical       Refresh
*0   1920 x 1200   ( 518mm x 324mm )  *60  
 1   3840 x 1200   ( 518mm x 324mm )   60  
 2   2560 x 1024   ( 518mm x 324mm )   60  
 3   1920 x 1080   ( 518mm x 324mm )   60  
 4   1600 x 1200   ( 518mm x 324mm )   60  
 5   1680 x 1050   ( 518mm x 324mm )   60  
 6   1280 x 1024   ( 518mm x 324mm )   60  
 7   1280 x 960    ( 518mm x 324mm )   60  
 8   1024 x 768    ( 518mm x 324mm )   60  
 9    800 x 600    ( 518mm x 324mm )   60  
 10   640 x 480    ( 518mm x 324mm )   60  
 11   720 x 400    ( 518mm x 324mm )   70  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis

```

---

### Post by papibe on 2014-08-07
Thanks.

It seems xrandr recognizes two devices: eDP1 and DP1 (I hope there are not logically the same, though).

Try this:
```
xrandr --output eDP1 --mode 1920x1200 --right-of DP1
```
You may try the reverse too:
```
xrandr --output DP1 --mode 1920x1200 --right-of eDP1
```
If that doesn't work, could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [pastebin.ubuntu.com]("http://pastebin.ubuntu.com/"), and then post back the link.

Regards.

---

