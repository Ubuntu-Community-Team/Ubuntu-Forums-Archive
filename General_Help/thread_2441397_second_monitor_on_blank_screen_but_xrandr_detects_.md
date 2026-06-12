---
title: "second monitor on blank screen but xrandr detects it (Ubuntu 20.04 - Nvidia)"
date: 2020-04-23
forum: General Help
---

### Post by noctis13 on 2020-04-23
For some reason, the second monitor connected via HDMI is in black (black screen), but xrandr and Nvidia Settings detects it.

```
  Screen 0: minimum 8 x 8, current 2720 x 1080, maximum 16384 x 16384
eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080 60.00*+ 59.97 59.96 59.93
   1680x1050 59.95 59.88
   1600x1024 60.17
   1400x1050 59.98
   1600x900 59.99 59.94 59.95 59.82
   1280x1024 60.02
   1440x900 59.89
   1400x900 59.96 59.88
   1280x960 60.00
   1440x810 60.00 59.97
   1368x768 59.88 59.85
   1360x768 59.80 59.96
   1280x800 59.99 59.97 59.81 59.91
   1152x864 60.00
   1280x720 60.00 59.99 59.86 59.74
   1024x768 60.04 60.00
   960x720 60.00
   928x696 60.05
   896x672 60.01
   1024x576 59.95 59.96 59.90 59.82
   960x600 59.93 60.00
   960x540 59.96 59.99 59.63 59.82
   800x600 60.00 60.32 56.25
   840x525 60.01 59.88
   864x486 59.92 59.57
   800x512 60.17
   700x525 59.98
   800x450 59.95 59.82
   640x512 60.02
   720x450 59.89
   700x450 59.96 59.88
   640x480 60.00 59.94
   720x405 59.51 58.99
   684x384 59.88 59.85
   680x384 59.80 59.96
   640x400 59.88 59.98
   576x432 60.06
   640x360 59.86 59.83 59.84 59.32
   512x384 60.00
   512x288 60.00 59.92
   480x270 59.63 59.82
   400x300 60.32 56.34
   432x243 59.92 59.57
   320x240 60.05
   360x202 59.51 59.13
   320x180 59.84 59.32
DP-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 connected 800x600+1920+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080 60.00 + 50.00 59.94 30.00 25.00 24.00 29.97 23.98
   1920x1080i 60.00 50.00 59.94
   1280x1024 60.02
   1360x768 60.02
   1152x864 59.97
   1280x720 59.81 60.00 50.00 59.94
   1024x768 60.00
   800x600 60.32*
   720x576 50.00
   720x576i 50.00
   720x480 60.00 59.94
   640x480 60.00 59.94
   720x400 70.08
DP-1-2 disconnected (normal left inverted right x axis y axis)
HDMI-1-3 disconnected (normal left inverted right x axis y axis)
```

I tried with propietary drivers of Nvidia and Nouveau's drivers, and I have the same result.  On Ubuntu 18.04 with the LTS Kernel (4.15 was?) works perfectly. Same with Windows 10. Since 19.10 it doesn't work. 
  The nvidia-drm modeset is on 0 (nvidia-drm modeset=0).
  Laptop: Asus Intel: i5-6300 Graphic card: Nvidia GTX960m


PD: With "nomodeset" it works. Don't know if that can helps.

---

