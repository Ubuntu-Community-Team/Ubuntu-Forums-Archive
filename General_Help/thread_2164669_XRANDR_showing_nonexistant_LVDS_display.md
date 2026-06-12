---
title: "XRANDR showing nonexistant LVDS display"
date: 2013-08-01
forum: General Help
---

### Post by ben-Nabiy_Derush on 2013-08-01
We have a computer lab with LTSP on 13.04.

When the clients connect to the server, the display resolution is very low, and the login looks like it is off the screen to the right.
When I log in, the client shows the desktop, but no menus. 

If I issue xrandr -q, I get:
```
$xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 32767 x 32767
LVDS1 connected (normal left inverted right x axis y axis)
   1024x768       60.0 +
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
$
```

And if I look in the Monitors pane in system config, it shows two displays, one called LAPTOP and one with the name of the monitor I am using, and the two are set to mirror. I have to disable the mirror, turn off the laptop screen, and reset the resolution for the monitor each time I log in. 

The thin client is an HP st5742 (thin client, not laptop).

On a different thin client, I tried through the display port and got the same result. Displayport is the HDMI1, VGA is VGA1 and there is nothing else on the machine to plug into.

---

### Post by ben-Nabiy_Derush on 2013-08-08
Well, the solution I found was to disable the LVDS display at boot.

```
append ro initrd=initrd.img-3.8.0-26-generic init=/sbin/init-ltsp quiet splash plymouth:force-splash vt.handoff=7 root=/dev/nbd0 video=LVDS-1:d
```

Appending the "video=LVDS-1:d"  does the magic .

---

