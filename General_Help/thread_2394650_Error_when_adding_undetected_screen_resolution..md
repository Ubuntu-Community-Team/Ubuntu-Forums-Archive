---
title: "Error when adding undetected screen resolution."
date: 2018-06-19
forum: General Help
---

### Post by debderivs on 2018-06-19
Hey guys,

When trying to add an undetected resolution, I get the following error. What is wrong? anything missing?
Not sure if I did all the correct steps in the process. Please, check the log below.

Thanks in advance!

```

DVI-I-3 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+  59.94    50.00    60.00    50.04  
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94    59.93  
   480x576       50.00  
   480x480       59.94  

~$ cvt 1600 900 60
# 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync

xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync

xrandr --addmode DVI-I-3 1600x900_60.00


~$ xrandr --addmode DVI-I-3 1600x900_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34

~$ xrandr --output DVI-I-3 --mode 1600x900_60.00
xrandr: cannot find mode 1600x900_60.00


```

---

