---
title: "HDMI does not work on freshly installed Ubuntu 18.04 LTS"
date: 2019-03-17
forum: General Help
---

### Post by tabularasa1234 on 2019-03-17
Hello, I have just recently installed Ubuntu and my external Monitor connected through HDMI does not work. I tried various tips found on internet (including installing nvidia drivers), but none work. I dual-boot with Windows on which HDMI works like a charm. I would be thankful for any tips for solving this issue.

---

### Post by Autodave on 2019-03-17
Try turning the monitor on and letting it stabilize before powering the PC.  I have had some luck this way.

What Nvidia card do you have?  What driver did you install and where did you get it from?  Some specs on your machine may help.

---

### Post by tabularasa1234 on 2019-03-18
> [COLOR=#000000]Try turning the monitor on and letting it stabilize before powering the PC. I have had some luck this way.[/COLOR]

[COLOR=#000000]I tried it and it didn't work.
[/COLOR]
> [COLOR=#000000]What Nvidia card do you have? What driver did you install and where did you get it from? Some specs on your machine may help.[/COLOR]

The Nvidia card is GTX 1050Ti, the laptop is Lenovo Legion Y530. I installed driver "NVIDIA driver metapackage from nvidia-driver-415 (open source)" from "Software & Updates" program "Additional Drivers" tab.

---

### Post by Autodave on 2019-03-18
Have you gone into settings to see if the monitor is recognized?  I had one once that I would have to go into that, disable the monitor and then re-enable it.  Then, it would sometimes work. :-)

---

### Post by tabularasa1234 on 2019-03-18
When I plug HDMI the laptop does not recognize the monitor/HDMI. The output of xrandr with plugged/unplugged cable is the same:
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
XWAYLAND0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 340mm x 190mm
   1920x1080     59.96*+

---

### Post by tabularasa1234 on 2019-03-21
_Bump_

---

