---
title: "Screen Resolution Not Autodetected"
date: 2017-04-11
forum: General Help
---

### Post by jmaciak1987 on 2017-04-11
This is a bit of a strange issue. I built two identical machines with the following embedded board: [http://www.asrock.com/mb/Intel/J4205-ITX/index.us.asp](http://www.asrock.com/mb/Intel/J4205-ITX/index.us.asp)

I installed Lubuntu 16.10 on both. When I plugged the first machine into a 1080p LED Sharp TV using an HDMI cable, it autodetected 1920x1080 as the max resolution. Great! Keep in mind I didn't have to install any additional Intel graphics drivers. For the second machine, I plugged it into a Samsung 4K TV using an HDMI cable. When it boots, it lists 1024x768 as the maximum resolution. Huh?

I installed and uninstalled the usual xserver-xorg-video-intel package, I've also installed the Intel driver update tool from: [https://01.org/linuxgraphics/downloads/update-tool](https://01.org/linuxgraphics/downloads/update-tool)

No dice.

The only way I can get to a higher resolution is to do the following: 
```
cvt 1920 1080 60
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DP-1 1920x1080_60.00
```
That will add 1920x1080 to the Screen Resolution app and then I can select it and all is well, until I reboot of course.

I've tried adding 3840x2160 as well, but it doesn't do anything....it just stays at 1920x1080. Of course, if I reboot, these settings don't stick as expected. I've tried adding the modes to /usr/share/X11/xorg.conf.d/10-monitor.conf, but then my system doesn't boot past the fsck.

What gives?

---

### Post by jmaciak1987 on 2017-04-12
Bump...

---

### Post by jmaciak1987 on 2017-04-18
Anyone?

---

