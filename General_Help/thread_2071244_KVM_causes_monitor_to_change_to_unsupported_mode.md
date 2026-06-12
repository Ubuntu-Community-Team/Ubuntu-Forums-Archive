---
title: "KVM causes monitor to change to unsupported mode"
date: 2012-10-14
forum: General Help
---

### Post by sienile on 2012-10-14
When switching my KVM between 2 Ubuntu PCs, one of them gets switched to an unsupported video mode and I have to blind-type the shutdown command to get it to reboot into it's proper mode.

I've seen many threads with this problem, but none with a solution. Is there one?

Is there a program that can select the refresh rates of the monitor?

---

### Post by Tralce on 2012-10-15
I've had a similar (but not identical) problem. Every time the machine booted up it would auto set to 640x480. I used a script to overcome it:
```
# use cvt to get a modeline to put here. 
# ex cvt 1280 1024 60
xrandr --newmode "1280x1024" 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024
xrandr --output VGA1 --mode 1280x1024
```
If you can tweak that to your needs you could probably assign it to a keystroke or timed event...

---

### Post by sienile on 2012-10-16
Sounds good. I've never used xrandr and don't want to screw things up to where I can't see to correct them. What are all the numbers after the resolution for in the newmode command?

---

### Post by Tralce on 2012-10-16
In my experience, everything you do with xrandr is temporary, hence the script. 

Use the cvt command to get your modeline. For example if you need your display set to 1280x1024, type in a terminal: (followed by the output)
```
tralce@eli:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```
That last line is your modeline. Remove the word "Modeline" from it  and paste it on the end of the xrandr command, for example:
```
xrandr --newmode "1280x1024" 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```
Tweak the rest of the script so that the rest of the names (I use 1280x1024 as a name for this example) match the name of your new mode, which will be in quotes at the beginning of the modeline. Run the script. Should automatically change your resolution settings. Run it whenever you have the resolution issue.

---

### Post by sienile on 2012-10-17
Thanks for the info. Might come in handy one day.

For now I've got the solution. This script is mapped to my KVM switch button.
```
#!/bin/bash

xrandr --output CRT1 --mode 1440x900
```

Turns out it was just changing the mode, not erasing the mode.

---

