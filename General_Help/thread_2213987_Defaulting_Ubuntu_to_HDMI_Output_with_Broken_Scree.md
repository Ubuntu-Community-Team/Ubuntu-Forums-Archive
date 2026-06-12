---
title: "Defaulting Ubuntu to HDMI Output with Broken Screen"
date: 2014-03-29
forum: General Help
---

### Post by jared15 on 2014-03-29
I have a laptop that has been sitting in my closet for sometime. Everything works except the screen which does not come on. I just installed Ubuntu 13.10 on the hard drive via an external case on my main computer. Everything went fine but when I try to plug the HDMI cord from my TV to the computer I get nothing. Seeing as the screen is broken, I cannot navigate or see anything in order to change options or even log in. Is there any process to maybe switch an option on Ubuntu so that when it boots up, it defaults to the HDMI output instead of the normal screen. Keep in mind, I have a second computer that works so it is possible for me to work with the hard drive that has Ubuntu installed. Any help would be greatly appreciated

---

### Post by TheFu on 2014-03-29
The video card matters - so do the drivers.

Can you ssh into the machine and make changes?

**xrandr** will let you set options for the different displays. Here's how I do it on my XBMC machine - over ssh.
```
$ export DISPLAY=:0
$ xrandr 
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1280x720+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       59.8 +
   1920x1080      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1776x1000      50.0     59.9     25.0     24.0     30.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       59.8  
   1280x768       59.8  
   1280x720       60.0*    50.0     59.9  
   1024x768      120.0     75.0     70.1     60.0  
   1152x648       50.0     59.9  
   1024x600      120.0     75.0     70.1     60.0  
   800x600       120.0     72.2     75.0     60.3     56.2  
   800x480       120.0     72.2     75.0     60.3     56.2  
   720x480        30.0     60.0     30.0     59.9  
   640x480        75.0     72.8     67.0     60.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)

```
It is currently connected to a 800p projector via HDMI.

BTW - thanks for the question - it got me to change the 720p output to 800p (native resolution) in the settings. Everything is just a little sharper.

---

