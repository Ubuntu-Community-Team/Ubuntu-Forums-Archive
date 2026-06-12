---
title: "Mouse flickering on one display"
date: 2017-01-30
forum: General Help
---

### Post by koop4 on 2017-01-30
[COLOR=#111111][FONT=Ubuntu]I've a  laptop ASUS N55SF with 2 external monitor connected, and the mouse pointer keep flickering when i click ore mouve it around on one of the two monitor. [/FONT][/COLOR]

[LIST]
[*]Os: ubuntu 16.04 LTS
[*]second monitor works fine (HDMI connected)
[*]video card nVidia 555M
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Additional Driver Tab: 
[/FONT][/COLOR][IMG]https://i.stack.imgur.com/KLYf2.png[/IMG]

[COLOR=#111111][FONT=Ubuntu]xrandr:
```
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]&#10140;  ~ xrandr[/FONT][/COLOR]
    Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767
    LVDS1 connected (normal left inverted right x axis y axis)
       1920x1080     60.00 +  59.93  
       1680x1050     59.88  
       1600x1024     60.17  
       1400x1050     59.98  
       1600x900      60.00  
       1280x1024     60.02  
       1440x900      59.89  
       1280x960      60.00  
       1368x768      60.00  
       1360x768      59.80    59.96  
       1152x864      60.00  
       1280x720      60.00  
       1024x768      60.00  
       1024x576      60.00  
       960x540       60.00  
       800x600       60.32    56.25  
       864x486       60.00  
       640x480       59.94  
       720x405       60.00  
       640x360       60.00  
    VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
       1920x1080     60.00*+
       1680x1050     59.95  
       1600x900      60.00  
       1280x1024     60.02  
       1440x900      59.89  
       1024x768      60.00  
       800x600       60.32  
       640x480       60.00  
       720x400       70.08  
    VIRTUAL1 disconnected (normal left inverted right x axis y axis)
    HDMI-1-1 connected primary 1920x1080+1920+0 509mm x 286mm
       1920x1080     60.00*+  50.00    59.94  
       1920x1080i    60.00    50.00    59.94  
       1680x1050     59.88  
       1600x900      60.00  
       1280x1024     60.02  
       1440x900      59.90  
       1280x720      60.00    50.00    59.94  
       1024x768      60.00  
       800x600       60.32  
       720x576       50.00  
       720x480       60.00    59.94  
       640x480       60.00    59.94  
       720x400       70.08  
      1920x1080 (0x43) 148.500MHz +HSync +VSync
            h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
            v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
      1680x1050 (0x49) 119.000MHz +HSync -VSync
            h: width  1680 start 1728 end 1760 total 1840 skew    0 clock  64.67KHz
            v: height 1050 start 1053 end 1059 total 1080           clock  59.88Hz
      1600x900 (0x4a) 108.000MHz +HSync +VSync
            h: width  1600 start 1624 end 1704 total 1800 skew    0 clock  60.00KHz
            v: height  900 start  901 end  904 total 1000           clock  60.00Hz
      1280x1024 (0x4b) 108.000MHz +HSync +VSync
            h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
            v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
      1024x768 (0x50) 65.000MHz -HSync -VSync
            h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
            v: height  768 start  771 end  777 total  806           clock  60.00Hz
      800x600 (0x51) 40.000MHz +HSync +VSync
            h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
            v: height  600 start  601 end  605 total  628           clock  60.32Hz
      640x480 (0x55) 25.200MHz -HSync -VSync
            h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
            v: height  480 start  490 end  492 total  525           clock  60.00Hz
      640x480 (0x56) 25.175MHz -HSync -VSync
            h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
            v: height  480 start  490 end  492 total  525           clock  59.94Hz
      720x400 (0x57) 28.320MHz -HSync +VSync
            h: width   720 start  738 end  846 total  900 skew    0 clock  31.47KHz
            v: height  400 start  412 end  414 total  449           clock  70.08Hz


[COLOR=#111111][FONT=Ubuntu]
```


[/FONT][/COLOR]

---

### Post by DuckHook on 2017-01-30
Welcome to the forums, koop4

Does it behave this way with the nouveau driver?

It is probably not a good idea to test this by changing drivers for now. Rather, first, run your laptop on a LiveUSB (which uses nouveau by default) and see if this behaviour persists.

You may also wish to consider installing the microcode for your CPU. Although the issues are unlikely to be related, there is a remote possibility that this could be the cause. You will have to reboot to allow the microcode to load.

---

