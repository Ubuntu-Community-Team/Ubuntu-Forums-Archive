---
title: "Triple Monitor Problems - How Can I Save Current Config?"
date: 2018-01-05
forum: General Help
---

### Post by mydroog on 2018-01-05
Hey everyone,

I am currently running Xubuntu 16.04.3 LTS

I  am having a terrible time getting 3 monitors functioning properly.  There is always some weird stuff going no, fragmentation, overlap,  clicking on one monitor and it registering on another, and so forth. I  almost abandoned this distro. 

However, after some sheer luck, I  managed to get them all organized properly using the "Display" app from  whisker menu, and messing about for 30 minutes. Somehow, after moving  them around and turning them on and off, it finally registered  correctly. The problem is that if I restart, these settings are gone,  and upon boot I once again have fragmentation, overlap, and just general  mayhem across the 3 screens. I should also mention that I tried forever  to make it work using the Nvidia drivers and their settings, which  ultimately failed, and I did a clean re-install. Now I'm on the XOrg  Nouvea video drivers. I am running 2 Nvidia GTX660s in SLI mode, with 2  monitors connected to one GPU, and the 3rd monitor connected to the  second GPU. 

Is there a way to export, save, and apply the  current settings? I'm not sure what this "Display" app changes exactly,  but here is the current output from the "xrandr" command.

```


Screen 0: minimum 320 x 200, current 5440 x 1080, maximum 16384 x 16384
DVI-I-1 connected 1920x1080+3520+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     60.00*+
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08  
HDMI-1 connected primary 1920x1080+1600+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+  50.00    59.94  
   1680x1050     59.88  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.90  
   1280x800      59.91  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
   720x400       70.08  
DP-1 disconnected (normal left inverted right x axis y axis)
DVI-D-1 disconnected (normal left inverted right x axis y axis)
DVI-I-1-2 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 connected 1600x900+0+180 (normal left inverted right x axis y axis) 442mm x 249mm
   1600x900      60.00*+
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08  
DP-1-2 disconnected (normal left inverted right x axis y axis)
DVI-D-1-2 disconnected (normal left inverted right x axis y axis)
  1600x900 (0x48) 108.000MHz +HSync +VSync
        h: width  1600 start 1624 end 1704 total 1800 skew    0 clock  60.00KHz
        v: height  900 start  901 end  904 total 1000           clock  60.00Hz
  1280x800 (0x49) 71.000MHz +HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock  49.31KHz
        v: height  800 start  803 end  809 total  823           clock  59.91Hz
  1152x864 (0x4a) 108.000MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock  67.50KHz
        v: height  864 start  865 end  868 total  900           clock  75.00Hz
  1280x720 (0x4b) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1024x768 (0x4c) 78.750MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.02KHz
        v: height  768 start  769 end  772 total  800           clock  75.03Hz
  1024x768 (0x4d) 75.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock  56.48KHz
        v: height  768 start  771 end  777 total  806           clock  70.07Hz
  1024x768 (0x4e) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  832x624 (0x4f) 57.284MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock  49.73KHz
        v: height  624 start  625 end  628 total  667           clock  74.55Hz
  800x600 (0x50) 50.000MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock  48.08KHz
        v: height  600 start  637 end  643 total  666           clock  72.19Hz
  800x600 (0x51) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x52) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x53) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x54) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x55) 31.500MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock  37.86KHz
        v: height  480 start  489 end  492 total  520           clock  72.81Hz
  640x480 (0x56) 30.240MHz -HSync -VSync
        h: width   640 start  704 end  768 total  864 skew    0 clock  35.00KHz
        v: height  480 start  483 end  486 total  525           clock  66.67Hz
  640x480 (0x57) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  720x400 (0x58) 28.320MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock  31.47KHz
        v: height  400 start  412 end  414 total  449           clock  70.08Hz




```


EDIT:

To answer my original question, I could save the current format by downloading Arandr, a GUI for Xrandr, and exporting the current setup to get the proper command to set the screen.
However, that wasn't what solved my problem in the optimal fashion.
I went ahead and installed the newest proprietary Nvidia drivers. Under XDisplay Configuration, after pressing "advanced", you get the option to "enable base mosaic", which should let you properly configure and enable the 3rd monitor. 
The configuration boots properly 100% of the time with no compromises
I am running 2 x Nvidia GTX660 in SLI Mode, 2 monitors connected to the first card, and one monitor connected to the second.
Xubuntu 16.04.3

---

### Post by oldfred on 2018-01-05
It has been years since I had to manual edit xorg, but your settings look like it. I thought they were doing away with xorg but some settings may still require it.
What does this show?

cat /etc/X11/xorg.conf 

If that is not it, then I do not know where else to look.

---

### Post by mydroog on 2018-01-05
> **oldfred said:**
> It has been years since I had to manual edit xorg, but your settings look like it. I thought they were doing away with xorg but some settings may still require it.
What does this show?

cat /etc/X11/xorg.conf 

If that is not it, then I do not know where else to look.

Thank you for the quick response.

I don't have an xorg.conf file in that directory for some reason.

I also found another interesting thing. If I boot the computer up, all the screens are completely messed up. However, if I then hibernate it, and turn it back on again, the structure is ALMOST perfect. With the exclusion of my leftmost monitor having icons on it that are beyond the screen (and it's not a resolution issue, because I can't move my mouse up there either). I feel as though perhaps this monitor turns on slowly in the boot up process, and that messes something up.

---

### Post by pqwoerituytrueiwoq on 2018-01-05
if that (display power on lag time) is the problem i know a single command that will fix it
this is the command i use when my TV is off when i wake from sleep mode to get my screen working (i use a button on my raspberry pi to send this via ssh)
[FONT=courier new]DISPLAY=":0.0" xrandr --output HDMI-0 --auto[/FONT]
maybe you can use something like [FONT=courier new]xrandr --auto[/FONT]
or maybe you need to tell each output to run auto separately
[FONT=courier new]xrandr --output DVI-I-1 --auto
[/FONT][FONT=courier new]xrandr --output HDMI-1 --auto
[/FONT][FONT=courier new]xrandr --output HDMI-1-2 --auto[/FONT]
worse case you can wire a 3 line script to configure your displays

if you close Xorg you can make a Xorg config file [FONT=courier new]Xorg -configure[/FONT] and edit your setting into it
maybe some here would be able to help you config it, all the numbers i think are in the xrandar output you posted
```

DVI-I-1    1920x1080+3520+0
HDMI-1     1920x1080+1600+0
HDMI-1-2   1600x900+0+180

```

---

### Post by mydroog on 2018-01-05
> **pqwoerituytrueiwoq said:**
> if that (display power on lag time) is the problem i know a single command that will fix it
this is the command i use when my TV is off when i wake from sleep mode to get my screen working (i use a button on my raspberry pi to send this via ssh)
[FONT=courier new]DISPLAY=":0.0" xrandr --output HDMI-0 --auto[/FONT]
maybe you can use something like [FONT=courier new]xrandr --auto[/FONT]
or maybe you need to tell each output to run auto separately
[FONT=courier new]xrandr --output DVI-I-1 --auto
[/FONT][FONT=courier new]xrandr --output HDMI-1 --auto
[/FONT][FONT=courier new]xrandr --output HDMI-1-2 --auto[/FONT]
worse case you can wire a 3 line script to configure your displays

if you close Xorg you can make a Xorg config file [FONT=courier new]Xorg -configure[/FONT] and edit your setting into it
maybe some here would be able to help you config it, all the numbers i think are in the xrandar output you posted
```

DVI-I-1    1920x1080+3520+0
HDMI-1     1920x1080+1600+0
HDMI-1-2   1600x900+0+180

```

My current script that I run at startup is: ```
xrandr --output DVI-D-1-2 --off --output HDMI-1-2 --mode 1600x900 --pos 0x180 --rotate normal --output DVI-I-1-2 --off --output HDMI-1 --primary --mode 1920x1080 --pos 1600x0 --rotate normal --output DVI-D-1 --off --output DVI-I-1 --mode 1920x1080 --pos 3520x0 --rotate normal --output DP-1-2 --off --output DP-1 --off
```

Seems to work, but I need to log in. Screen is all garbled. But if I lock my PC using ctrl+alt+del and log in again, the issue is fixed. Initial boot is really messed up though, makes me think that perhaps the monitor powers on too slowly or something?

What does the --auto argument do? Can I add it to my current startup script (I just run this command through the "session and startup" app in Xubuntu. While look into injecting the xorg config file)

---

### Post by pqwoerituytrueiwoq on 2018-01-05
auto just set the display to its auto detected settings, so you do not need to define 1920x1080 for example
save your command to a .sh file and drop it in /usr/local/bin/
* line 1 should be "[FONT=courier new]#!/bin/sh[/FONT]" do not forget to [FONT=courier new]chmod +x[/FONT] it
then edit (or create) this file
/etc/lightdm/lightdm.conf
then put these 2 file below the "[FONT=courier new][SeatDefaults][/FONT]" line
[FONT=courier new]greeter-setup-script=/usr/local/bin/myScript.sh
session-setup-script=/usr/local/bin/myScript.sh[/FONT]

now your displays should be set at the login screen then again after login
there is a [FONT=courier new]display-setup-script[/FONT] script you could define, may be useful?

you may want to put this script on a keyboard shortcut for easy access

since you have a command to fix it you could exit the x session and generate a Xorg.conf file and post it here and we can tweak it to hold your settings and have Xorg apply it automatically

---

