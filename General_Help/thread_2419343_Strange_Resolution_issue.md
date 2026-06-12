---
title: "Strange Resolution issue"
date: 2019-05-20
forum: General Help
---

### Post by rkurnik on 2019-05-20
I have two 4k monitors.  one is a 24" dell and the other is a 32" Samsung curved.  I am aslo using a MSI gforce 1060 6G card.

So the issue I am having is it seems the Samsung monitor is does not have the resolution that it is reporting.  Both monitors are set to 3840x2160.  The 32" is set to landscape mode and the other is portrait.  On moving windows from one screen to the other it is clear that the samsung has a lower resolution.

I have two 27 uhd at my office and the resolutions and window sizes match perfectly. What I mean is the window is the same size in either screen.

Here's the xrandr output:

 home-desktop:~$ xrandrScreen 0: minimum 8 x 8, current 7080 x 3840, maximum 32767 x 32767
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 2160x3840+0+0 right (normal left inverted right x axis y axis) 527mm x 296mm
  3840x2160     29.98*+  30.00    29.97    25.00    23.98
  2560x1440     59.95
  2048x1280     60.00
  1920x1080     60.00    60.00    59.94    50.00    29.97    25.00    23.98    60.05    60.00    50.04    50.04
  1600x1200     60.00
  1600x900      60.00
  1280x1024     75.02    60.02
  1280x720      59.94    50.00
  1152x864      75.00
  1024x768      75.03    60.00
  800x600       75.00    60.32
  720x576       50.00
  720x480       59.94
  640x480       75.00    59.94    59.93
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected primary 3840x2160+2160+639 (normal left inverted right x axis y axis) 697mm x 392mm
  3840x2160     30.00*+  29.97    25.00    23.98
  2560x1440     59.95
  1920x1080     60.00    59.94    50.00    29.97    23.98
  1680x1050     59.95
  1600x900      60.00
  1440x900      59.89
  1280x1024     75.02    60.02
  1280x800      59.81
  1280x720      60.00    59.94    50.00
  1152x864      75.00
  1024x768      75.03    70.07    60.00
  800x600       75.00    72.19    60.32    56.25
  720x576       50.00
  720x480       59.94
  640x480       75.00    72.81    59.94
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 connected 1080x1920+6000+879 left (normal left inverted right x axis y axis) 531mm x 299mm
  1920x1080     60.00*+
  1280x1024     75.02    60.02
  1152x864      75.00
  1024x768      75.03    60.00
  800x600       75.00    60.32
  640x480       75.00    59.94

I've also included a screen shot of the problem.  Agin both screens report 3840x2160


Also I swapped the cables and the ports and that did not help.

---

### Post by dino99 on 2019-05-20
I does not know if your cpu/msi card are able to manage both 4k devices at once. Maybe test with only one 4 k at a time to see if the problem persist.
Do you find some warnings/errors from 'journalctl -b' ?

Note: i've read somwhere that mutter does not cope well with 144 K (maybe related)

---

