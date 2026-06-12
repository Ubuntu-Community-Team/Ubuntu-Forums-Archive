---
title: "Adding a third monitor in 16.04LTS unity desktop"
date: 2017-01-25
forum: General Help
---

### Post by leeko on 2017-01-25
Hi all,

I am working on a fresh install of ubuntu 16.04 LTS, and have everything working as it should with the exception of my monitor setup. I have an nvidia 840GS video card, and am attempting to run 3 monitors. 

My primary monitor is a 27" dell, attached via onboard HDMI output. Everything is working very nicely there. 
2nd monitor is an unbranded 15" flatpanel, attached via VGA out on the nvidia card. Working fine. 
3rd monitor is an acer 19" flatpanel, attached via DVI output on the video card. Not working properly. 

The ubuntu unity desktop loads, and the first 2 monitors display correctly. the 3rd monitor remains in standby. Interestingly, during bootup, the display is at various times shown on each of the 3 monitors - just not on the 3rd after the display manager starts. 

I attempted to switch to the recommended nvidia driver using ubuntu's inbuilt utility, but it made a huge mess and forced me into recovery mode. I'm now back to nouveau, and would like to try getting the monitor to display using that if possible. 

The display config graphical utility has some weird quirks for me - for example, I can't position the monitors where I want them - there are invisible barriers within the dialog. The 3rd monitor is detected and shown, but when I attempt to enable it, I get a timeout message. A second error message pops up saying 

"The selected configuration for displays could not be applied. could not set the configuration for CRTC 64"

I tried arandr, and get the following error:

"XRandR failed:
XRandR returned error code 1: X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Value in failed request:  0x0
  Serial number of failed request:  49
  Current serial number in output stream:  50"

Here is the output from xrandr --query

```
leeko@leekodesktop:~$ xrandr --query
Screen 0: minimum 8 x 8, current 4640 x 1080, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1080+1280+0 (normal left inverted right x axis y axis) 597mm x 336mm
   1920x1080     60.00*+  60.00    50.00    59.94    24.00    23.98  
   1920x1080i    60.00    50.00    59.94  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.08    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
VGA-1-2 connected 1280x1024+0+0 340mm x 270mm
   1280x1024     75.02* 
   1024x768      75.08    72.00    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    70.01    60.32    56.25  
   640x480       75.00    72.81    66.67    70.03    60.00    59.94  
   720x400       70.08  
DVI-I-1-1 connected
   1440x900      59.89 +
   1600x1200     60.00  
   1400x1050     59.95  
   1280x1024     60.02  
   1280x960      60.00  
   1152x864      75.00    59.97  
   1280x720      60.00  
   1024x768      75.08    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    60.00  
   720x400       70.08  
HDMI-1-2 disconnected
  1280x1024 (0x45) 135.000MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock  79.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  75.02Hz
  1024x768 (0x46) 78.800MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.06KHz
        v: height  768 start  769 end  772 total  800           clock  75.08Hz
  1024x768 (0x49) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x4c) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x4e) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  640x480 (0x50) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x54) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
  640x480 (0x55) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  720x400 (0x56) 28.320MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock  31.47KHz
        v: height  400 start  412 end  414 total  449           clock  70.08Hz
  1600x1200 (0x58) 162.000MHz +HSync +VSync
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock  75.00KHz
        v: height 1200 start 1201 end 1204 total 1250           clock  60.00Hz
  1280x1024 (0x5a) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1152x864 (0x5c) 108.000MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock  67.50KHz
        v: height  864 start  865 end  868 total  900           clock  75.00Hz
  1280x720 (0x5e) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz

```

I'm not sure what to do next. Any help you can offer in troubleshooting this would be much appreciated.

Thanks,

Lee

---

### Post by leeko on 2017-01-26
Bumping thus back to the top. I appreciate any help offered, 

Thanks

Lee

---

### Post by denfordberriman on 2017-07-24
Have you managed to get this working?
I'm trying to do the same but haven't found a good guide on how to yet.

Here's my xrandr output.

```

Screen 0: minimum 8 x 8, current 1920 x 2160, maximum 16384 x 16384
eDP-1-1 connected primary 1920x1080+0+1080 344mm x 194mm
   1920x1080     60.02*+  59.93    48.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
DP-1-1 disconnected
HDMI-1-1 disconnected
DP-1-2 connected 1920x1080+0+0 477mm x 268mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x720      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
   720x400       70.08  
HDMI-1-2 disconnected



```

---

### Post by wildmanne39 on 2017-07-24
Welcome to the forum, please start your own thread so you can get the help you need.

Thanks

---

