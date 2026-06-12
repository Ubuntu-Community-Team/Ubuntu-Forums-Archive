---
title: "xandr/screenclone timeout"
date: 2013-10-07
forum: General Help
---

### Post by xluke on 2013-10-07
Hello,
Using a tutorial I got my display to extend to an led display through displayport using this script:
#!/bin/bash
optirun true 
##(this starts the xserver and the settings you've modded above will prevent bumblebee from shutting it off)
xrandr --output LVDS1 --mode 1360x768 --output VIRTUAL --mode 1360x768 --right-of LVDS1
##(this activates the virtual screen on the intel chip - a 1440x900 external display placed to the right of the laptop's internal display)
screenclone -d :8 -x 1

However, I can not get the extended display to not timeout.  I've adjusted settings in main ubuntu to keep the main display from timing out, but the extended display times out after ten minutes.  Is there a way to alter this script to eliminate screen timeout on the extended display?

I'm grateful for any tips!
Thanks!

---

