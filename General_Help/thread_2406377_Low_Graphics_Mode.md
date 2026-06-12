---
title: "Low Graphics Mode"
date: 2018-11-20
forum: General Help
---

### Post by daniell59 on 2018-11-20
Sometimes when I boot up, I get a message that I am running low in graphics mode. I would appreciate it if somebody would explain to me what is happening, and how to remedy the problem.

Ubuntu 16.04 64

---

### Post by NM5TF on 2018-11-20
do you have a nvidia graphics card ???

post the output of

```
inxi -G
```

tommy

---

### Post by daniell59 on 2018-11-20
Card: Advanced Micro Devices [AMD/ATI] RV620 LE [Radeon HD 3450]
           Display Server: X.Org 1.19.6 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1680x1050@59.88hz
           GLX Renderer: AMD RV620 (DRM 2.50.0 / 4.15.0-39-generic, LLVM 6.0.0)
           GLX Version: 3.0 Mesa 18.0.5

---

### Post by NM5TF on 2018-11-20
your resolution of 1680 x 1050 is not a standard resolution recommended by the MFR....
specs here [https://www.techpowerup.com/gpu-specs/radeon-hd-3450.c224]("https://www.techpowerup.com/gpu-specs/radeon-hd-3450.c224")

did you set it yourself ??

have you tried using xrandr to set it to 1920 x 1080 ??

tommy

---

### Post by daniell59 on 2018-11-20
> **NM5TF said:**
> your resolution of 1680 x 1050 is not a standard resolution recommended by the MFR....
specs here [https://www.techpowerup.com/gpu-specs/radeon-hd-3450.c224]("https://www.techpowerup.com/gpu-specs/radeon-hd-3450.c224")

did you set it yourself ??

have you tried using xrandr to set it to 1920 x 1080 ??

tommy

I did not set it myself. I don't know what xrandr is.
Thank you for your assistance.

---

### Post by NM5TF on 2018-11-20
if you want to set it for full HD try this....

```
xrandr
```

you will see something like this...

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

and then do this

```
cvt 1920 1080
```

you will see something like this...

```
[tommy@tommy ~]$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

copy the info [COLOR="#FF0000"]WITHOUT MODELINE[/COLOR] & make a new mode like this..

```
 xrandr --new mode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

and then add the new mode to your display....[COLOR="#FF0000"]in my case it is VGA-1, yours may be different[/COLOR] your monitor is
what shows up in xrandr output....

```
xrandr --addmode VGA1 1920 x1080_60.00

```

and finally do this

```
xrandr --output VGA1 --mode 1920 x 1080_60.00

```

Note that these settings only take effect during this session. If you are pleased with the results, you need to make it permanent.
Once a suitable resolution is found using xrandr, the mode can be permanently added by creating an entry in /etc/X11/xorg.conf

something like this should work

```

Section "Monitor"
    Identifier "VGA1"
    Modeline "1920 x 1080_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    Option "PreferredMode" "1920 x 1080_60.00"
EndSection

Section "Screen"
    Identifier "Screen0"
    Monitor "VGA1"
    DefaultDepth 24
    SubSection "Display"
        Modes "1920 x 1080_60.00"
    EndSubSection
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
EndSection
```

[COLOR="#FF0000"]change Monitor "VGA-1" to whatever your monitor's ID is from xrandr
[/COLOR]
[COLOR="#FF0000"]also change Driver "intel" to "ati,radeon"[/COLOR]

info about xrandr is found here [https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected]("https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected")

hope this helps

tommy

---

### Post by daniell59 on 2018-11-20
Thanks for your informative reply. There is a lot for me to digest. When my concentration is better, I will begin the process. Under ideal conditions, should this be an automatic process? Is the video card too old for this task?



> **NM5TF said:**
> if you want to set it for full HD try this....

```
xrandr
```

you will see something like this...

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

and then do this

```
cvt 1920 1080
```

you will see something like this...

```
[tommy@tommy ~]$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

copy the info [COLOR="#FF0000"]WITHOUT MODELINE[/COLOR] & make a new mode like this..

```
 xrandr --new mode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

and then add the new mode to your display....[COLOR="#FF0000"]in my case it is VGA-1, yours may be different[/COLOR] your monitor is
what shows up in xrandr output....

```
xrandr --addmode VGA1 1920 x1080_60.00

```

and finally do this

```
xrandr --output VGA1 --mode 1920 x 1080_60.00

```

Note that these settings only take effect during this session. If you are pleased with the results, you need to make it permanent.
Once a suitable resolution is found using xrandr, the mode can be permanently added by creating an entry in /etc/X11/xorg.conf

something like this should work

```

Section "Monitor"
    Identifier "VGA1"
    Modeline "1920 x 1080_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    Option "PreferredMode" "1920 x 1080_60.00"
EndSection

Section "Screen"
    Identifier "Screen0"
    Monitor "VGA1"
    DefaultDepth 24
    SubSection "Display"
        Modes "1920 x 1080_60.00"
    EndSubSection
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
EndSection
```

[COLOR="#FF0000"]change Monitor "VGA-1" to whatever your monitor's ID is from xrandr
[/COLOR]
[COLOR="#FF0000"]also change Driver "intel" to "ati,radeon"[/COLOR]

info about xrandr is found here [https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected]("https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected")

hope this helps

tommy

---

### Post by NM5TF on 2018-11-20
my system is older than yours....2007 build with older nvidia GeForce 6150se card...

if you successfully follow the above procedure, it will be automatic from now...

yours should be no problem...

tommy

---

