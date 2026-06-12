---
title: "edit xorg"
date: 2016-05-23
forum: General Help
---

### Post by hooman3 on 2016-05-23
Hi All!

i have a monitor with 1280x1024 resolution, but in ubuntu its set on 1024x768 and no other settings available. i can add correct resolution but after each reboot its back. i try to edit xorg.conf for too times from a lot of threads but not working. now what can i do?

lspci | grep VGA:
```

01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4200]

```

xrandr:
```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DisplayPort-0 disconnected (normal left inverted right x axis y axis)

```

Thank you !!

---

### Post by oldos2er on 2016-05-23
Moved to General Help.

Which version of Ubuntu are you using?

---

### Post by hooman3 on 2016-05-23
16.04 lts

---

### Post by grahammechanical on 2016-05-23
You have a VGA connection from the video adapter to the monitor. VGA is very old technology that limits the screen resolution because it was designed years before these digital monitors with their much high resolutions were manufactured. You might get higher resolutions if you used the Displayport connection.

I am getting 1920 x 1080 with a HDMI connection. But I know from experence that if I used a VGA connection I would only get 1024 x 768.

Regards.

---

### Post by efflandt on 2016-05-24
It is not VGA that limits the screen resolution, it is that Linux cannot tell what analog video is capable of like it can for digital video, so usually all it offers is some 4:3 aspect ratio PC modes. I have used xrandr in a script to set VGA modes on a laptop as high as 1920x1080 for an external HDTV (or 1360x768 with a really low end laptop). But I am not sure how to do that automatically for X or in xorg.conf. And sometimes you have to make adjustments if not perfectly sized or centered.

First you use **cvt** or **gtf** to get examples of modelines:```
efflandt@XPS-8100-1404:~$ cvt 1280 1024 60
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

efflandt@XPS-8100-1404:~$ gtf 1280 1024 60
  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
```Then you can plug each of those into a script to try them out to see which works better:```
#!/bin/sh
# Set resolution
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA-0 1280x1024_60.00
xrandr --output VGA-0 --mode 1280x1024_60.00
```

---

### Post by bcschmerker on 2016-05-24
**Thanks for this Topic on fine-tuning GPU transmissions.**  I'm looking over the problem of altering timings from a DVI-D or HDMI output on an ATi® Radeon®-based video display adapter to make an RCA® L26HD31R flat-screen TV, that has historically chopped off the left side and pillarboxed the right side of the GPU output, display correctly.  What would be the default modeline for Mode 1280x720_60.00 in Xorg.conf (alternately XF86.conf)?  The figures will give me a starting point for the adjustments outlined above.

---

