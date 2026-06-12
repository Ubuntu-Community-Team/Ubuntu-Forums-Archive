---
title: "Gaming Graphics with ATI"
date: 2007-04-29
forum: General Help
---

### Post by jonnymccullagh on 2007-04-29
I installed Feisty on my new laptop (with ATI Radeon x1600 256Mb Graphics Card), although I had to install the fglrx drivers at the command line just to get the livecd to run.
Now I have feisty but the performance of games is very poor. Very jerky and impossibly slow graphics in SuperTux and Slune. I have tried these games on my desktop (Edgy + ATI Radeon 9600) and they work as expected. 
Has anyone any ideas on how I could get more power from my graphics card? (I appreciate that ATI/AMD need to open up their drivers ;-) )
Thanks in advance,
jonny

---

### Post by madmetal on 2007-04-29
open a terminal and give
glxinfo | grep direct
to see if direct rendering is on 
and if yes then 
glxgears
to see its performance..
thats my nVidia fx5500 results..

10102 frames in 5.0 seconds = 2020.354 FPS
14593 frames in 5.0 seconds = 2918.588 FPS
15629 frames in 5.0 seconds = 3114.882 FPS
14805 frames in 5.0 seconds = 2960.872 FPS

---

### Post by jonnymccullagh on 2007-04-29
I get:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

I assume I am doing something wrong. Do I need to amend something in my xorg.conf ?

---

### Post by madmetal on 2007-04-29
> **jonnymccullagh said:**
> I get:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

I assume I am doing something wrong. Do I need to amend something in my xorg.conf ?

i dont think you have Ati drivers installed..
look whats on system >>  administration >> restricted drivers manager

---

### Post by jonnymccullagh on 2007-04-30
I have the ATI driver appearing in Restricted Drivers but the tickbox for enabled is not ticked but the Status shows as 'In Use' - I'm confused - what does the enabled tick box actually do?
I have the fglrx driver installed via synaptic - Does that do the install but not enable the driver?

---

### Post by jonnymccullagh on 2007-04-30
No need to reply - thanks for the help - I ticked the enabled box and and it is working well.
I just wish I could get the Desktop Effects but I get a "The Composite extension is not available" - time for some searches,
thanks,
j

---

### Post by aldenhg on 2007-04-30
If you want the Desktop Effects to work and you're using fglrx, you need to disable compositing. Open up a terminal and enter ```
sudo gedit /etc/X11/xorg.conf
``` then add these lines to the bottom of the file: ```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```
and after an X restart everything should be good.

---

### Post by jonnymccullagh on 2007-04-30
Thanks,
I still couldn't get it working though. My xorg.conf already had:
```
Section "Extensions"
	Option	    "Composite" "0"
EndSection
```
I changed the 0 to Disabled as you suggested and restarted X but I get the same error message when trying to enable desktop effects.
Thanks for your help though,
j

---

### Post by aldenhg on 2007-05-01
Huh. That usually solves it. I don't know about Compiz (that's what the desktop effects are provided by), but Beryl (a fork of Compiz that is now being re-integrated) doesn't work with the fglrx driver without XGL. Are you using XGL or the vanilla Xorg server that comes with Ubuntu?

---

### Post by strabes on 2007-05-01
```
sudo apt-get update && sudo apt-get install xorg-driver-fglrx && sudo depmod -a && sudo aticonfig --initial && sudo aticonfig --overlay-type=Xv
```

Then add this to the bottom of your xorg.conf: > Section "Extensions"
        Option      "Composite" "0"
EndSection

Taken from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

