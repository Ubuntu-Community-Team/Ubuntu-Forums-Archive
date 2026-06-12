---
title: "Set secondiary monitor as primary for fullscreen apps / games"
date: 2014-04-10
forum: General Help
---

### Post by Xanthius on 2014-04-10
To start, I have an notebook with an optimus card and it took me some time to get things working but I have little knowledge of what my system is currently using as a display driver; as in would I use the nvidia control panel or do I change settings in the xorg config. Sad thing is I'm afraid to touch it cause the last time I messed around with it I broke things... which resulted in a reinstall.

**The issue:**
[LIST]
[*]Full screen games are being displayed on my integrated monitor, instead of the secondary one.
[*]Some flash players also only pop up on my integrated monitor in full screen
[/LIST]

**The setup:**
Left is the notebook, right is the secondary monitor connected with a mDP.
```
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 32767 x 32767
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1920x1080      60.0*+   59.9     40.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1080+1920+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080      59.9*+   60.0  
   1680x1050      59.9  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

Strange thing here, to my knowledge the mDP is connected with the intel side of the optimus architecture as it is with the LVDS.
Only the HDMI is connected directly with the nvidia graphics card, with no screen connected anyways.
So I'm guessing that I am not using the nVidia drivers, and that I need to change things in the xorg settings.

**What I've done:**
[LIST]
[*]People recommended PUT, enable it assign a hotkey. Well I guess my keys must be broken cause no screen is moving anywhere.
[*]Change the primary monitor, ... no comment. Really this feature doesn't change --anything--
[*]Mostly searching for an issue, but the most relevant I could find is the flash player issue.
[*]Installed PPAPI for flashplayer, using chromium obviously then.
[/LIST]

Again, I am reluctant to change display drivers cause I don't want to upset my primusrun cause breaking this is my specialty. It happened multiple times. 

So doctors, what's the prognosis?

---

### Post by Xanthius on 2014-04-11
I still need help with this issue

---

### Post by Xanthius on 2014-04-13
Kinda still need input..

---

### Post by Xanthius on 2014-04-14
[Any help]("http://a.gifb.in/15g6454656.gif") is appreciated :(

---

