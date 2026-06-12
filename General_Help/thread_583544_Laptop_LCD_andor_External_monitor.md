---
title: "Laptop LCD and/or External monitor"
date: 2007-10-20
forum: General Help
---

### Post by kbracer on 2007-10-20
Laptop is a Fujitsu S6120 with...

[LIST]
[*]Gutsy 7.10 fresh install
[*]Intel 855GM Video
[*]Laptop LCD 1024x768
[*]External LCD Samsung 226BW 1680x1050
[/LIST]

The behavior I desire...

[LIST]
[*]When not docked use native 1024x786 on lappy LCD.
[*]When docked use the external at 1680x1050.
[/LIST]
When docked I don't care what the lappy LCD is doing. It could be off, scaling, panning, or whatever.

I have tried various settings with Gutsy's "Screen and Graphics" settings - no hand mangling of xorg.conf yet. I've tried using the i810 driver and the Intel modesetting driver. I have not been able to get consistent and predictable behavior. It seems offer up different resolution options every time I restart the system or the X server. It looks like it often wants to do the proper resolution for the external monitor, but is trying to use too high a refresh rate that results in no display. 

The closest I have gotten results in the external LCD using 1680x1050 and the lappy LCD showing the top-left 1024x768 of the desktop without panning or scrolling. This would be fine except for the fact that the windows on the desktop want to conform to the 1024x768 dimension when they are maximized - meaning they do not use the whole desktop on the 1680x1050 external lcd.

Is there some known solution for my configuration and desired behavior? 

I will post up my xorg.conf when I have access to my lappy later, although it is just the default generated conf and probably all knackered by my playing in "Screens and Graphics".

---

