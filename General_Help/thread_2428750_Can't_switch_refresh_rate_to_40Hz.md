---
title: "Can't switch refresh rate to 40Hz"
date: 2019-10-08
forum: General Help
---

### Post by NovHak on 2019-10-08
Dear forum readers,

My 2014 laptop isn't quite new, and when I run demanding games, I sometimes resort to switching my refresh rate from 60 to 40Hz, while setting VSync at the same time. It has the advantage of limiting the frame rate and at the same time prevents tearing, of course.

At least, that's what I do on Windows...

However, trying to do the same on my Ubuntu 19.04, xrandr indeed says a 40Hz mode is selected, the Xorg server log mentions the switch as an informational entry, but I can tell it hasn't switched. My standard test is moving the cursor across the screen at a certain speed, that way one can tell the refresh rate difference... and as I feared, the game shows 60fps with VSync enabled.

To rule out Optimus-specific problems as much as possible, I've run "prime-select intel" and my Nvidia GTX 880M GPU isn't used any more (the dGPU light remains off).

Now I do my testing with the AssaultCube game (apt install assaultcube) that is far less demanding (and has a built-in fps counter and a VSync option), since I could not even dream of the other game running on the iGPU for efficient testing. And the problem is still there : 60fps with VSync on after switching to 40Hz. However, I noticed that minimising/enlarging windows is more jittery, so it must have an impact somehow. I play in windowed, mode, not full screen, just to be sure.

I tried creating a new 40Hz mode :

```
~$ cvt 1920 1080 40
# 1920x1080 39.96 Hz (CVT) hsync: 44.27 kHz; pclk: 110.50 MHz
Modeline "1920x1080_40.00"  110.50  1920 2016 2208 2496  1080 1083 1088 1108 -hsync +vsync
~$ xrandr --newmode "My_mode" 110.50  1920 2016 2208 2496  1080 1083 1088 1108 -hsync +vsync
~$ xrandr --addmode eDP1 My_mode
~$ xrandr --output eDP1 --mode My_mode     # I tried with/without the "--rate 40" option
```

but trying to switch to it, the screen goes blank for a few seconds and reverts to the previous mode. In the Xorg log I can see two switches :

```
[ 45637.086] (II) intel(0): switch to mode 1920x1080@40.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 45639.278] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
```

Here are the gathered Modelines :

```
[ 38614.460] (II) intel(0): EDID vendor "CMO", prod id 5920
[ 38614.460] (II) intel(0): Printing DDC gathered Modelines:
[ 38614.460] (II) intel(0): Modeline "1920x1080"x0.0  140.49  1920 1972 2007 2094  1080 1083 1089 1118 +hsync -vsync (67.1 kHz eP)
[ 38614.460] (II) intel(0): Modeline "1920x1080"x0.0   92.45  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (44.4 kHz e)
```

Any ideas to have this computer to actually switch to 40Hz ? Your suggestions are welcome...

EDIT : My hardware : CPU : i7-4710MQ (Intel HD Graphics 4600), GPU : Nvidia GTX 880M, 16 GiB RAM (fwiw)

---

