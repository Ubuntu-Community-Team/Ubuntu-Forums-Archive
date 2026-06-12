---
title: "Poor Graphics Perfomance"
date: 2007-12-26
forum: General Help
---

### Post by dink1000 on 2007-12-26
Right now i've sort of sorted out how to get this hdd to work after having to have to take it out of my previous pc.

things is that now all the graphics are really choppy (2D and 3D)

this is what i got from lspci

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)

so think i might not have the right drivers installed as i used to have a nvidia card in the pc the hdd came out of.

also glxgears i get this.
-desktop:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
271 frames in 8.2 seconds = 32.959 FPS
240 frames in 9.0 seconds = 26.814 FPS
240 frames in 9.0 seconds = 26.669 FPS

i've tried dpkg-reconfigure xserver-xorg but didn't know which to pick out of the list.

---

### Post by overdrank on 2007-12-26
> **dink1000 said:**
> Right now i've sort of sorted out how to get this hdd to work after having to have to take it out of my previous pc.

things is that now all the graphics are really choppy (2D and 3D)

this is what i got from lspci

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)

so think i might not have the right drivers installed as i used to have a nvidia card in the pc the hdd came out of.

also glxgears i get this.
-desktop:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
271 frames in 8.2 seconds = 32.959 FPS
240 frames in 9.0 seconds = 26.814 FPS
240 frames in 9.0 seconds = 26.669 FPS

i've tried dpkg-reconfigure xserver-xorg but didn't know which to pick out of the list.

HI and you can try and search in synaptic manager for intel and install the 915 resolution. Then if all else fails reconfigure your xorg with this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by dink1000 on 2007-12-26
right now i've tried chaging to the intel driver but it doesn't seem to work properly(the login screen isn't center of the monitor and the resolution is not right once it is logged in and it wont change to 1280x1024)

but it seems to be fine if i select the i810 driver in xserver-xorg.

also if i boot to the failsafe GNOME is seems to work fine. i get the right resolution no error in glxgears and about 800 FPS rather than 35 FPS.

---

