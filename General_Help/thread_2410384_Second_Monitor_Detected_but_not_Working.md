---
title: "Second Monitor Detected but not Working"
date: 2019-01-14
forum: General Help
---

### Post by groundwaterwill on 2019-01-14
Hello. I just upgraded my motherboard and CPU, and installed a new version of Xubuntu, and now my second monitor says "there is no signal coming from the computer". It's a VGA monitor connected to a DVI port via an adapter. I already tried switching to the Nvidia drivers, running updates, doing sudo apt-get upgrade, restarting, and poking around in the display settings. The settings say that they do recognize the monitor, and the computer accepts that monitor as having space (I can move the cursor into the area there), but there is no signal still, and the poor monitor remains black. I have also tried using a different computer with the monitor, which returns no issues. There were no such issues here until today. Please help me as to fix this problem.

---

### Post by groundwaterwill on 2019-01-14
Additionally, if I have my headphones plugged in through the HDMI monitor, I can hear fine. However, once the DVI monitor is even plugged in, the audio output ceases, even if they're still plugged into the HDMI monitor!

---

### Post by groundwaterwill on 2019-01-14
BTW, the output for xrandr is as follows:

```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DVI-D-0 connected 1600x900+0+0 (normal left inverted right x axis y axis) 434mm x 236mm
   1600x900      59.98*+  60.00  
   1920x1080     59.94  
   1280x1024     75.02    60.02  
   1280x720      59.94  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x480       59.94    59.94  
   640x480       75.00    59.94  
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+  59.94    50.00    23.98    60.05    60.00    50.04  
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94    59.93  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)



```

---

