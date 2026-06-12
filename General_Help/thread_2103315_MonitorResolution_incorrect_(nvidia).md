---
title: "Monitor/Resolution incorrect (nvidia)"
date: 2013-01-09
forum: General Help
---

### Post by crashh on 2013-01-09
I installed Ubuntu 12.04 and have been struggling for hours trying to  figure out how to get nvidia to detect my monitor. When I first  installed Ubuntu, I opened the 'Additional Drivers' and installed the  version-current option and rebooted. Nothing changed, although in  additional drivers it tells me that that driver is activated.

My monitors resolution is meant to be 1600x900 and is connected via VGA  (the monitor is a HP 2009v), but it can only be set up to 1024x768. My  graphics card is an nvidia 9500GT.

This is my 'xrandr' output:
```
xrandr: Failed to get size of gamma for output default 
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768 
default connected 1024x768+0+0 0mm x 0mm 
1024x768       50.0*  
800x600        51.0     52.0     53.0   
680x384        54.0     55.0   
640x480        56.0   
512x384        57.0
400x300        58.0 
320x240        59.0
```I  also tried 'nvidia-settings' but the only monitor that is detected  is a CRT-0 on GPU-0, except I can change the resolution to 1360x768  (though it appears off screen for some reason).  I'm really not sure what the problem is - as far as I am aware, I  have up-to-date drivers but nothing is working. From what I've used of  Ubuntu it seems really great so far, but this is definitely something  that is making me think twice about using it. Windows had no problem  detecting my monitor.
  Any help (if possible) would be greatly appreciated!

EDIT:
I just rebooted a few times and, for some reason, my monitor is now detected! I'm not quite sure what happened - I'm sorry if anyone with a similar problem sees this, I can't provide you with a solution because I don't know what happened!
Sorry if this post seems irrelevant now, please delete it if necessary.

---

