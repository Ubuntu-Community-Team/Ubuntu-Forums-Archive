---
title: "After update, I can't see my second monitor"
date: 2019-03-10
forum: General Help
---

### Post by jfca283 on 2019-03-10
Hello, 
I recently updated my ubuntu 18.04.
Now, I can't use my two screens. The one I had as primary shows no image.
Under nvidia-settings, I can edit some preferences of the screen. But no mattar what I edit, the screen looks only black.
What can I do?
This is what xrandr shows:
```
juan@juan-OptiPlex-7010:~$ xrandr 
Screen 0: minimum 8 x 8, current 2966 x 900, maximum 8192 x 8192
DVI-I-0 connected 1600x900+1366+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1600x900      59.82* 
   1400x900      59.88  
   1368x768      59.88    59.85  
   1360x768      59.96    59.80  
   1280x800      59.91    59.81  
   1280x720      59.86    59.74  
   1152x864      60.00  
   1024x576      59.90    59.82  
   960x540       59.82    59.63  
   864x486       59.92    59.57  
   800x600       72.19    60.32    56.25  
   800x450       59.82  
   700x450       59.88  
   684x384       59.88    59.85  
   680x384       59.96    59.80  
   640x480       59.94  
   640x400       59.98    59.88  
   640x360       59.86    59.83  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.82    59.63  
   432x243       59.92    59.57  
   400x300       72.19  
   320x240       60.05  
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 413mm x 234mm
   1366x768      59.79*+
   1920x1080     59.94  
   1280x1024     60.02  
   1280x960      60.00  
   1280x720      60.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x480       59.94    59.94  
   640x480       59.94  

```
Thank you for your time and interest.

---

### Post by pqwoerituytrueiwoq on 2019-03-10
Blank or no signal? have you verified the monitor is set to he correct input
I assume your DVI monitor is the one having a issue
which nvidia gpu and driver version are you using?

I had a issue similar the other week with a GT 430 and a monitor, it would not work if turned on via the disper command, but it worked fine using xrandr

---

### Post by jfca283 on 2019-03-11
Hi, 
I think it was a driver issue.
I changed the nvidia driver for the native one.
That recovered the monitor with the black screen, but I lost the one which was working ok.
Then I changed, again, the driver for the nvidia.
Now both screen show image. So, I know it was a driver issue, but I have no idea the reason the screens are ok.

---

