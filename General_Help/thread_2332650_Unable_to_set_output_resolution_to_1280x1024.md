---
title: "Unable to set output resolution to 1280x1024"
date: 2016-08-02
forum: General Help
---

### Post by b3ware on 2016-08-02
Hi,

I accidentally sat on the screen of my Sony Vaio laptop and crushed it, so I'm now using a DGM L-1731 monitor on the VGA output. Thing is, the monitor is capable of showing a maximum resolution of 1280x1024, but the only option available in the screen display utility is 1024x768. After testing the monitor on a Windows machine, I found it was running 1280x1024 at 60Hz.

After doing a few searches I found that I needed to do something along the lines of:
```
cvt 1280 1024 60
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode 1280x1024_60.00

```

However, after executing the last command, the screen blanks for a second and then returns with no change in resolution. I also wondered if there was an issue with drivers, and since I have Intel integrated graphics, I headed to Intel's website to download their update utility. However, the tool is only compatible with Ubuntu 15.10 and below.

I'm pretty stuck for ideas. Could someone shine a light on this?

EDIT:
Solved my problem. Turns out the HSYNC and VSYNC polarities from cvt were wrong.

---

