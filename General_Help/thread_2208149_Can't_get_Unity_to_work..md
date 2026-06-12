---
title: "Can't get Unity to work."
date: 2014-02-26
forum: General Help
---

### Post by cenzo2 on 2014-02-26
I'm a bit new to ubuntu, Crunchbang tends to be my linux distro of choice. But this computer has a touchscreen and I felt like Ubuntu would be a better OS for that. I don't even know if I'll be able to make the touchscreen play nice with the OS yet, though. But I've just installed it on this older PC that I have. First thing I noticed, running from the live CD, was the lack of a taskbar and window borders. I installed the OS anyway, but now when I log in I don't have a taskbar or window borders, and I can't move or resize windows. Before I log in, I can see that there is a taskbar like there should be. But once I log in, that disappears and I'm left with only a desktop and the hotkeys. 
I tried ```
[COLOR=#333333][FONT=UbuntuRegular]dconf reset -f /org/compiz/[/FONT][/COLOR]
``` and then ```
[COLOR=#333333][FONT=UbuntuRegular]setsid unity[/FONT][/COLOR]
``` with no success. 
Here's the output of setsid unity:
```
root@carthage:~# setsid unityroot@carthage:~# compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
root@carthage:~# compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.


compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.


compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
```

---

### Post by oldos2er on 2014-02-26
From this > compiz (core) - Error: Plugin 'opengl' not loaded. I'm guessing it's a video issue. What video card is in the system, and have you checked if it has Additional Drivers available? ```
software-properties-gtk
```

---

### Post by cenzo2 on 2014-02-26
No additional drivers seem to be available. Video card is a bit of a complicated issue here. See we're not exactly dealing with a PC, it's an old NCR point-of-sale terminal (found in the garbage) with a build-in 15" monitor with a capacitive touchscreen. I figured that working with such an unusual device might cause a me some problems. I'm not sure if it's considered on-board video or not, there is a card of some sort installed that's labeled "LVDS board" and connected to the screen.

---

### Post by oldos2er on 2014-02-27
You might want to try a different desktop environment that doesn't require or can easily run without OpenGL, such as xfce or lxde.

---

### Post by cenzo2 on 2014-03-01
> **oldos2er said:**
> You might want to try a different desktop environment that doesn't require or can easily run without OpenGL, such as xfce or lxde.

xfce worked very well for me. It all seems to be working now. Thanks.

---

