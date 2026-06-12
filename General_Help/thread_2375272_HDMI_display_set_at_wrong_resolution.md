---
title: "HDMI display set at wrong resolution"
date: 2017-10-23
forum: General Help
---

### Post by marianknot on 2017-10-23
Hello everyone!
I'm having some problems with my second HDMI extended display on Ubuntu 16.04. It's correctly detected by the OS, but when i enter to the monitor menu, it shows it has a resolution of "4 x 512". The display stretches to 4px width, and I can't find a way to fix it.

 In the ubuntu settings, its set to 1366x768.

The kernel i'm using is 4.12.13-041213-generic.

On Windows 10 it works perfectly so i know it's an issue with Linux and my current HW

Here is the output of xrandr:

Screen 0: minimum 320 x 200, current 2732 x 768, maximum 8192 x 8192
HDMI-1 connected 1366x768+1366+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1366x768      60.00*+
   1920x1080     60.00    50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     75.02  
   1360x768      60.02  
   1280x800      59.91  
   1280x720      60.00    50.00    59.94  
   1440x576      50.00  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768      59.66 +
   1366x768      60.00* 
   1280x768      59.72  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   640x480       75.00    72.81    59.94  
   720x400       70.08  
HDMI-2 disconnected (normal left inverted right x axis y axis)


Any help will be very appreciated,
Thanks!

---

