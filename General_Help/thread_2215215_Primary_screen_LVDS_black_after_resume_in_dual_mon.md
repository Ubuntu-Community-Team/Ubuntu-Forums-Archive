---
title: "Primary screen LVDS black after resume in dual monitor configuration"
date: 2014-04-05
forum: General Help
---

### Post by hkskoglund on 2014-04-05
Hi, I sometimes get a black screen on my primary laptop monitor LVDS, and on the secondary monitor VGA-0 I get a window with "Could not change display configuration CRTC 79". What is CRTC 79?

Running xrandr:

```
Screen 0: minimum 320 x 200, current 3320 x 1080, maximum 8192 x 8192
VGA-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 886mm x 498mm
LVDS connected 1400x1050+1920+0 (normal left inverted right x axis y axis) 287mm x 215mm
DVI-0 disconnected (normal left inverted right x axis y axis)
```

shows that VGA-0 is now the primary monitor (this must have been set by the system, not by me)

To revert this situation I go to the  display settings in unity and turn on the LVDS screen again. But still the LVDS is not set as  primary screen. If I run

    ```
xrandr --output LVDS --primary
```

the terminal window if moved outside any monitor screen, and I have to type Alt-Space and move the window back again....

```
lshw -c video
  *-display               
       description: VGA compatible controller
       product: RV515/M54 [Mobility Radeon X1400]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
      

```

Ubuntu 13.10
Linux kernel : 3.11.0.-19-generic

Anyone else experinced this?

---

