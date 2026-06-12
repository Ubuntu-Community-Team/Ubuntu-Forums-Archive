---
title: "Screen Tearing"
date: 2018-11-14
forum: General Help
---

### Post by try431 on 2018-11-14
Hey there,

I followed the steps as described - I created a file "zz-nvidia-modeset.conf', added the line "options nvidia_drm modeset=1", and ran ```
sudo update-initramfs -u
```, then rebooted. The screen tearing is gone!

HOWEVER, now for some reason I can't connect to any of my monitors. The output of running `xrandr` is as follows:

```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767eDP-1-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     60.02*+  60.01    59.97    59.96    59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
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
DP-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-1 disconnected (normal left inverted right x axis y axis)
```


Has anyone else experienced issues with connecting to monitors after they've made this change? I'm running Ubuntu 18.04 on an MSI GE63 Stealth 8RE, with an NVIDIA GTX 1060.

---

### Post by slickymaster on 2018-11-14
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

Initial thread here: [https://ubuntuforums.org/showthread.php?t=2374405](https://ubuntuforums.org/showthread.php?t=2374405)

---

