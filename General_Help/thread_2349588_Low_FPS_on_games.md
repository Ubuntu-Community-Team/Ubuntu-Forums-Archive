---
title: "Low FPS on games"
date: 2017-01-16
forum: General Help
---

### Post by nandosen on 2017-01-16
Hello i just installed Ubuntu on my laptop that i dont use and now i am  having problems with FPS. 

Before I installed ubuntu I had windows 10. I  am having bad FPS on games like I had around 250 fps in Counter Strike  Source on my windows 10 but now I have 70 fps and around 100 fps on  Global Offensive now I have 30 FPS so whats the problem here? 

I am new  to ubuntu so I need to learn this more.

---

### Post by ajgreeny on 2017-01-16
What graphics hardware does the laptop have?

---

### Post by leandrort on 2017-09-08
[COLOR=#111111][FONT=Ubuntu]Hello, guys, I have the same problem, I'm using Lubuntu 16.04, it's a good system very fast and security. But I can't see videos with good quality and fast speed (action) or even play light games. I have an Intel Baytrail Processor (N2930), My graphic video card is an Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e). It's not the "intel_idle.max_cstate=1" issue. I tried to use the 4.11 Kernel, installed Oibaf Drivers, I have Mesa updated and all, but nothing increased the FPS.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I ran glxgears and that's the results:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
vblank_mode=0 glxgears[/FONT][/COLOR]

```
ATTENTION: default value of option vblank_mode overridden by environment.
1321 frames in 5.0 seconds = 264.145 FPS
1506 frames in 5.0 seconds = 301.098 FPS
1474 frames in 5.0 seconds = 294.780 FPS
1632 frames in 5.0 seconds = 326.380 FPS
1469 frames in 5.0 seconds = 293.576 FPS
1479 frames in 5.0 seconds = 295.740 FPS
1515 frames in 5.0 seconds = 302.824 FPS
1489 frames in 5.0 seconds = 297.684 FPS

```

[COLOR=#111111][FONT=Ubuntu]Fullscreen is worst than window mode[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
vblank_mode=0 glxgears -fullscreen[/FONT][/COLOR]
```
ATTENTION: default value of option vblank_mode overridden by environment.
303 frames in 5.0 seconds = 60.528 FPS
366 frames in 5.0 seconds = 73.026 FPS
353 frames in 5.0 seconds = 70.412 FPS
367 frames in 5.0 seconds = 73.226 FPS

```
[COLOR=#111111][FONT=Ubuntu]
This is my Xorg config[/FONT][/COLOR]
```
Section "Device"
   Identifier "Intel Graphics"
   Driver     "intel"
   Option     "NoAccel"   "True"
   Option     "DRI"       "False"
EndSection
```

[COLOR=#111111][FONT=Ubuntu]Thank you all, guys. Please, help me, I'm in love with Lubuntu, it's the only issue I found.[/FONT][/COLOR]

---

