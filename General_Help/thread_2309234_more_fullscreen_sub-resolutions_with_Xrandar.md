---
title: "more fullscreen sub-resolutions with Xrandar"
date: 2016-01-08
forum: General Help
---

### Post by Cæncel on 2016-01-08
basically what i want is more resolutions that maintain the correct aspect ratio of my screen, say instead of 4:3 800x600 i would rather use 16:9 800x450, Xrandar already knows some of my possible resolutions:

```
$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 16384 x 16384
VGA-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 410mm x 260mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
   720x400        70.1  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
```

so basically my problem here are 1024x678,800x600 and 640x480 which are on 4:3, it does really bother me because i run some games that don't really need the whole 1360x768 screen and run better in smaller resolutions, even those programs who allow me to set a custom resolution can't set it because xrandr sets the nearest resolution instead, example RedEclipse can use custom resolutions, if i set 1024x568 Xrandr will set 1024x768 instead, now while setting custom resolutions (about to set it to 1366x768 which is the right screen size) i noticed some settings

```
Modeline "1368x768R"   72.25  **1368 1416 1448 1528  768 771 781 790** +hsync -vsync
```

didn't took me long enough to figure out these may be resolution scales, in fact in one instance instead of scaling to higher resolutions i found an example of decreasing resolutions but i really need confirmation on this, and if i can modify these values so the xrandr list of resolutions change.

note, i don't want to change the main resolution of my desktop, just create a list of smaller resolutions available for games and apps on fullscreen with the right aspect ratio

thanks in advance

---

### Post by Cæncel on 2016-01-09
any help? please?

---

