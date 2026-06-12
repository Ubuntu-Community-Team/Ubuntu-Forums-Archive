---
title: "Screen Resolution Issue"
date: 2013-05-31
forum: General Help
---

### Post by MustangV10 on 2013-05-31
Hi,

I'm running Ubuntu 13.04. I have a laptop (main display) and a monitor connected via a VGA cable.

The monitor in question in question is an Acer P193W, and the resolution is: 1440 x 900 ([http://www.pcpro.co.uk/reviews/monitors/235998/acer-p193w/specifications](http://www.pcpro.co.uk/reviews/monitors/235998/acer-p193w/specifications)).

I manually added that resolution since it wasn't displayed before. I've tried a few different resolutions and the picture goes slightly off the screen. It seems like the picture on screen is too wide. Does anyone have any suggestions? I have attached a picture of my monitor and what I see. [ATTACH=CONFIG]243320[/ATTACH]

> $ xrandr
Screen 0: minimum 320 x 200, current 2800 x 900, maximum 32767 x 32767
LVDS1 connected 1360x768+0+132 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0 +
   1360x768       59.8*    60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1440x900+1360+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1440x900       59.9* 
   1400x900       60.0  
   1350x900       59.9  
   1450x900       59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        59.9 +
   640x480        59.9 +
   1024x768       59.9  
   800x600        59.9  

---

### Post by col48 on 2013-05-31
The default for my Iiyama was also too wide - alarming not to be able to see the button to log out etc!
Changing from 1680 to 1600 cured it.

> $ xrandr
Screen 0: minimum 320 x 200, current 1600 x 1000, maximum 4096 x 4096
VGA-0 connected 1600x1000+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9 +
   1600x1200      60.0  
   1600x1000      60.0* 
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1152x720       60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     66.7     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)



---

