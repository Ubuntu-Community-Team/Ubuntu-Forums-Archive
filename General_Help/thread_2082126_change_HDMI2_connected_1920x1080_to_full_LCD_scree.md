---
title: "change HDMI2 connected 1920x1080 to full LCD screen"
date: 2012-11-08
forum: General Help
---

### Post by workaround on 2012-11-08
Would anyone elaborate on the screen resolution/panning/mode/fb/... . I can set my ASUS LCD to 1920x1080 BUT it crams itself into upper-left side block of the full screen and so the apps icons do not go all the way down but they bunch up about 3 -4 inches from the bottom up and I got mail twice on my screen including the time, audio and icon for quick access as well!?
 I know I had it once correctly working (the entire monitor screen was one block) before I reinstalled Ubuntu and so I know it is possible but how? I did try several version of how but none did the trick of fixing it.
 

 Output from xrandr:
 HDMI1 disconnected (normal left inverted right x axis y axis) 
 HDMI2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm 
    1920x1080      60.0*+   50.0     60.0     25.0     30.0   
 

 Thanks much.:confused:

---

### Post by workaround on 2012-11-08
OK, it's working!
```
xrandr --output HDMI2 --mode 1920x1080 --rate 60 --fb 8192x8192
```:popcorn:

---

