---
title: "Can't change display settings when connected to tv"
date: 2013-12-20
forum: General Help
---

### Post by PDavis1248 on 2013-12-20
I am trying to connect my laptop to my tv. I selected to mirror the display. Unfortunately the only resolution option available for mirroring the display is 640x480. Now the display settings window doesn't even fit on the screen when I'm connected to the TV, and so I can't click the apply button to try to change the settings. It seems that if I'm using the GUI that I'm stuck in 640x480. Is there a way I can change these settings from the terminal? Ideally I would mirror the display still, but at a higher resolution. But if that isn't possible I'd at least like to stop it from mirroring the display, so I can have a usable resolution on each.

After a little searching I saw that I may be able to use xrandr to do this, but haven't had any success with it. It lists my display options as

Screen 0: minimum 320 x 200, current 640 x 480, maximum 8192 x 8192
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9* 
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 640x480+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1280x720       60.0 +
   720x480        59.9  
   640x480        60.0* 

It looks like from this that 640x480 is the only resolution my laptop and the TV have in common. And it won't let choose another size.

Any suggestions of how to fix this?

---

### Post by PDavis1248 on 2013-12-20
Figured it out. I was able to stop mirroring the screen with xrandr.

---

