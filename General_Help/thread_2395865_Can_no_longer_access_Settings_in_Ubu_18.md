---
title: "Can no longer access Settings in Ubu 18"
date: 2018-07-07
forum: General Help
---

### Post by sebastien4 on 2018-07-07
I just installed Ubuntu 18. Was setting it up. I moved the Doc to the bottom. Now for some reason When i open up Settings, it shows it is open with little red dot under icon, but the window does not open. I tried everything. Is this a bug??? Am I missing something here?

The only clue as to what is going on is when i open the app, there seems to be going on to right of screen. 

thanks.

---

### Post by deadflowr on 2018-07-07
> The only clue as to what is going on is when i open the app, there seems to be going on to right of screen. 

Phantom second monitor?
See if your system is showing itself a second monitor, xrandr show do.
See if it's something like this:
[https://askubuntu.com/questions/366813/disable-second-non-existent-screen-from-command-line]("https://askubuntu.com/questions/366813/disable-second-non-existent-screen-from-command-line")
Post the xrandr --current output if you don't understand it.

---

### Post by sebastien4 on 2018-07-08
worked. Below is the output. I turned off VGA-1-2. What a weird issue to have. Should have posted earlier. thank you.

```
xrandr --current
Screen 0: minimum 320 x 200, current 2390 x 768, maximum 8192 x 8192
LVDS-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1366x768      60.07*+
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
VGA-1-2 connected 1024x768+1366+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
  1024x768 (0x43) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x44) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x45) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x47) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
```

---

### Post by sebastien4 on 2018-07-08
So... I just logged out and logged back in, and same problem comes back. Tried to open settings and another app, and it goes to non existent screen. Is this glitch and is there a way to fix this permanently?

---

### Post by deadflowr on 2018-07-08
What you might do is after turning off the monitor vga1-2, open settings and go to Devices  >> Displays and try doubling down on the display setting there.
See if setting it there helps turn it off.

---

### Post by sebastien4 on 2018-07-09
Thank you. i will try once i get home.

---

