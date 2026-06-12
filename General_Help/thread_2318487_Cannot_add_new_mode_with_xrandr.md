---
title: "Cannot add new mode with xrandr"
date: 2016-03-26
forum: General Help
---

### Post by cranerja on 2016-03-26
Hello!

I am trying to add a resolution that my monitor (Seiki SE39UY04) is capable of doing. This is my xrandr output prior to trying to add a new mode:
```
$ xrandrScreen 0: minimum 8 x 8, current 3840 x 2160, maximum 16384 x 16384
DVI-I-0 connected (normal left inverted right x axis y axis)
   1366x768      59.79 +
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 698mm x 393mm
   3840x2160     30.00*+  29.97    25.00    23.98  
   1920x1080     59.94    50.00    23.97    60.05    60.00    50.04  
   1440x900      59.89  
   1280x960      60.00  
   1280x720      59.94    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    72.81    59.94  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)

```
I then run:
```
$ sudo xrandr --newmode "2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync

```
Then I run into this problem:
```
$ sudo xrandr --addmode HDMI-0 "2560x1440_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)  
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  39
  Current serial number in output stream:  40

```
But this is the strange part, my xrandr output after:
```
$ xrandrScreen 0: minimum 8 x 8, current 3840 x 2160, maximum 16384 x 16384
DVI-I-0 connected (normal left inverted right x axis y axis)
   1366x768      59.79 +
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 698mm x 393mm
   3840x2160     30.00*+  29.97    25.00    23.98  
   1920x1080     59.94    50.00    23.97    60.05    60.00    50.04  
   1440x900      59.89  
   1280x960      60.00  
   1280x720      59.94    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    72.81    59.94  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
  2560x1440_60.00 (0x200) 312.250MHz
        h: width  2560 start 2752 end 3024 total 3488 skew    0 clock  89.52KHz
        v: height 1440 start 1443 end 1448 total 1493           clock  59.96Hz

```

It adds the new mode to DVI-D-0. Why is it doing this? What else could I try?
Thanks in advance!

---

