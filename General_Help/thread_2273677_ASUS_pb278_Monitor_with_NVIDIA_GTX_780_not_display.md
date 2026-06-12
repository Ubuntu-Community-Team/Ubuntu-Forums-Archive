---
title: "ASUS pb278 Monitor with NVIDIA GTX 780 not displaying option for 2560x1440"
date: 2015-04-14
forum: General Help
---

### Post by maxwell3 on 2015-04-14
Have been looking for a fix for this since yesterday and after a good number of hours searching I finally decided to make a post about this. So as the title says in the NVIDIA settings panel there is no option for any resolution above 1920x1080 for my 2560x1440 monitor. Under additional drivers I have tried both proprietary NVIDIA drivers(331.113 & 331.113-updates), as well as Nouveau display drivers. Under NVDIDA x server settings I've tried changing the ViewportIn to 2560x1440 instead of 1920x1080, It does make the things on screen smaller (to scale as if it actually was the right resolution) but does not increase the resolution. Also my monitor is plugged into my card using the HDMI connector. I appreciate any help and would be incredibly grateful to anyone whom could help me solve this issue. If this is the wrong forum please let me know so I can delete/move the thread. Thanks!

Here is the output from xrandr:

```


Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 600mm x 340mm
   1920x1080      60.0*+   59.9     50.0     30.0     25.0     24.0     60.0     50.0  
   1680x1050      60.0  
   1440x900       59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0     59.9     50.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        75.0     59.9     59.9  
   480x576        50.0  
   480x480        59.9  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)


```

Here is the ouput for lspci | grep VGA

```


01:00.0 VGA compatible controller: NVIDIA Corporation GK110 [GeForce GTX 780] (rev a1)


```

---

