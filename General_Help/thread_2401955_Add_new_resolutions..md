---
title: "Add new resolutions."
date: 2018-09-24
forum: General Help
---

### Post by mazak23 on 2018-09-24
Hi.
I am going to work on two displays.
One is not showing higher resolution than 1024x768.
It tried to do it from this : [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
But there is no /etc/gdm folder.
I am on Xubuntu 18.04.1 LTS 4.15.0-34-generic
Can anybody point me in right direction?

---

### Post by idkwhatimdoing1.0 on 2018-09-24
hey, I have heard of many people having this kind of issue. Are you using a VGA cable? and if so (no judging) if you bought it from a sketchy/cheap place it is quite possibble that not every pins are connected. I would suggest trying another cable to see if the resolution is working fine and if not try using the setting app itself. Usually less of a drag.

---

### Post by mazak23 on 2018-10-03
I don't think it is the point. It is working manually, finally  I did script that I run, and I am very happy doing it myself:
> #!/bin/bash
xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA-1 1440x900_60.00
xrandr --output VGA-1 --mode 1440x900_60.00  

---

### Post by mazak23 on 2018-10-07
Anybody using Xubuntu and can tell me where to add this to be permanent?

---

### Post by NM5TF on 2018-10-07
just run this again...

```
xrandr
```

if your new mode shows up with an * next to it, you are good to go...might look like this...

```
[tommy@tommy ~]$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
VGA-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00*+
   1366x768      59.79  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   640x480       75.00    72.81    59.94  
   720x400       70.08  

```

if it is not there, you need to use xrandr to add new resolution...your script does that, but to make it
permanent do this without the bash script...

```
xrandr --newmode "1440x900_60.00" 106.50 1440 1528 1672 1904 900 903 909 934 -hsync +vsync
xrandr --addmode VGA-1 1440x900_60.00
xrandr --output VGA-1 --mode 1440x900_60.00
```



tommy

---

### Post by mazak23 on 2018-11-18
tommy
thanks for your help.
I did that what you wrote.
Unfortunately it is not stays there after restart.
Still the highest resolution I see is old 1024x786, there is no 1440x900 in these settings:

---

