---
title: "[SOLVED -sort of] mouse now constrained w: xrandr  --scale 1.28x1.25"
date: 2013-06-13
forum: General Help
---

### Post by maestrobwh1 on 2013-06-13
This started happening with Precise (worked for a while then one of the xorg package updates started constraining my mouse) and is persisting with Raring

When I issue this command

```
xrandr --output LVDS1 --scale 1.28x1.25
```

I am able to see the entire scaled screen BUT the mouse will not enter the new "virtual" area and is constrained to the original 1024x600 area.

In LXDE, I stopped compiz to see if that was the issue, but the problem persisted.

I have been fighting with this since early spring.  It happens in LXDE as well as Unity, so it is not a Unity issue alone.

I have a 1024x600 display in an Asus EEEPC 901

I have fiddled around with an xorg file /etc/X11/xorg.conf.d/20-intel.conf that I put there to enable "sna" over "exa" but the extra lines below that do not seem to help:

```
Section "Device"
 Driver  "Intel"
 Option  "AccelMethod" "sna"
 Option          "MigrationHeuristic" "greedy"
 Option          "TripleBuffer" "true"
EndSection

Section "Monitor"
       Identifier	"LVDS1"
       Option		"DPMS"
EndSection  

Section "Screen"
       Identifier	"Default Screen"
       Device		"Card0"
       Monitor		"LVDS1"
       DefaultDepth	24
   
       SubSection "Display"
           Depth		24
           Modes		"1024x600" "800x600" "640x480"
           Virtual              1600 1600 
       EndSubSection
EndSection
```

---

### Post by maestrobwh1 on 2013-06-24
Somewhat of a workaround; looks sloppy and panels do not extend themselves, and docky has to be killed or it ends up in the middle of the screen  BUT when I need more space, I can do this

```
xrandr --fb 1366x768 --output LVDS1 --scale 1.33x1.28
```

And in the compiz configuration manager under 
->general
->general settings
->display settings, add the --fb dimentions.

I had to use a proportion to calculate how to extend the 1024x600 screen to a silmilar proportioned screen.

---

