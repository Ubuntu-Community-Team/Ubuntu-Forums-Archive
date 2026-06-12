---
title: "External monitor goes black for a few seconds at random"
date: 2018-01-16
forum: General Help
---

### Post by marino2 on 2018-01-16
Hi,

I'm having a problem with my external monitor; I searched extensively for a solution online, but ultimately couldn't solve the problem, so I'm looking for help here.

I have a Dell Latitude 7480 running Ubuntu 16.04. The laptop is connected to a dock station, which in turn is connected to an external monitor (plus mouse and keyboard). Both dock station and monitor are also from Dell. I normally use the external monitor as the only display (the laptop is closed).

The problem is the monitor goes black for 2/3 seconds, then the image comes back; during this short period of time computer, mouse and keyboard work normally. This apparently happens at random (to give an idea, on a given day it can happen anywhere between zero and ten times). This does not happen when using the laptop on its own, so I'm guessing the problem has to do with the external monitor.

At times (again apparently at random) part of the monitor also flickers (not the full screen, it's more like a fine horizontal line in the middle of the screen).

There is one effect which is reproducible, but I don't know if it's related to the monitor blacking-out. When I log-in, I type the password, and, as soon as I press Enter, the hidden characters in the tab disappear and the graphics in the upper-half of the login page get distorted (after that, the Desktop gets displayed normally). Just like for the black-out problem, this effect does not occur when using the the lapton on its own.

It seems like every time the problem occurs the following X log-file gets updated: /var/log/Xorg.0.log

The problem appears with both VGA and DisplayPort (for the dockstation-monitor connection).

Below I copied the output of xrandr, to give some info on the screens.

Please let me know if you have any idea on what the issue could be, any help is greatly appreciated.

Thanks!

---------------------------------

```
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 32767 x 32767
eDP1 connected (normal left inverted right x axis y axis)
   1920x1080     60.05 +  59.93    48.04  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
DP1 disconnected (normal left inverted right x axis y axis)
DP1-1 disconnected (normal left inverted right x axis y axis)
DP1-2 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+
   1920x1080     60.00  
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     60.02  
   1280x960      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       60.00  
   720x400       70.08  
DP1-3 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by toregon on 2018-01-18
I had the same problem with my Lenovo X series laptop and docking with 3 monitors
After trying all kinds of stuff i borrowed a Lenovo x with windows ran the Lenovo system update for the docking station  ( it had 3 updates for the docking firmware )and voila   everything works a charm
no more flickering or random  monitor black out :)

---

### Post by marino2 on 2018-01-24
Thanks for your reply toregon, makes sense that the problem may be related to the dock station.

Just a side note (in case it helps anybody): in the last week I have stopped opening the "skypeforlinux" app, and the issue hasn't appeared once since then (still I can't be 100% sure that's what was causing the problem).

---

