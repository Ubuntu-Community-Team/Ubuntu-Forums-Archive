---
title: "installed lubuntu trying to run 3 monitors which seems like its impossible"
date: 2016-01-10
forum: General Help
---

### Post by edgar13 on 2016-01-10
Has anyone found a way to run the onboard and a graphic card at the same time? Ive searched and have not found any threads that would help me configure. I think its possible, when lubuntu starts up all 3 screens show the lubuntu logo but once the login screen come up only 2 monitors work and the 3rd is dark. any suggestions? all the settings show 2 monitors not 3.

also if i go from graphical to text my 3 monitor is the one that work.

heres some of the outputs ive gotten. 

```
e@1:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao PRO [Radeon R7 370 / R9 270/370 OEM]

e@1:~$ xrandr
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 16384 x 16384
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
DFP5 disconnected (normal left inverted right x axis y axis)
DFP6 connected 1680x1050+0+0 inverted (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050     59.95*+
   1400x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      75.02    60.02  
   1280x800      59.81  
   1152x864      59.95    75.00  
   1280x768      59.81  
   1280x720      59.86  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32    56.25  
   640x480       72.81    75.00    66.61    59.94  
DFP7 connected 1680x1050+1680+0 inverted (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050     59.95*+
   1400x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      75.02    60.02  
   1280x800      59.81  
   1152x864      59.95    75.00  
   1280x768      59.81  
   1280x720      59.86  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32    56.25  
   640x480       72.81    75.00    66.61    59.94  
CRT1 disconnected (normal left inverted right x axis y axis)
```

---

