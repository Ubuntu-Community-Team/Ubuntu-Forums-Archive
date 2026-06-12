---
title: "couple of video player niggles"
date: 2005-11-02
forum: General Help
---

### Post by pickarooney on 2005-11-02
1) I've always preferred mplayer to xine, but on Ubuntu mplayer goes out of synch on every file I play, and playback of WMV files is unwatchable (choppy).

2) Xine works a lot better, no asynching and WMVs play OK. But is there any way of getting rid of that silly Christmas splash screen. It's unnecessary, not to mention a little early/late :)

---

### Post by Kyral on 2005-11-02
VLC? Or combine Totem with Xine (totem-xine)

I don't use MPlayer so I can't help you with it :/

---

### Post by frodon on 2005-11-02
If you like xine, why not use the totem interface, the package is called totem-xine or you have also gxine.

---

### Post by Kyral on 2005-11-02
Didn't I just say that? ;P

---

### Post by pickarooney on 2005-11-02
totem-xine is installed, but how do I run it?
Is it just **totem** from the command line? (that takes about 30 seconds to open BTW, ouch)

---

### Post by pickarooney on 2005-11-03
I seem to be having video issues, playback being awfully slow with some files, but I don't know if it's to do with my gfx card or codecs. Can anyone help me with the following?

- in the HOWTO, the following appears, in relation to mplayer:
[i]Find this line 

...
vo=x11,                  # To specify default video driver (see -vo help for
...
Replace with the following line 

vo=xv,                  # To specify default video driver (see -vo help for[/i]

What exactly is this change specifying and what's the difference between xv and x11?

I have a nVidia GeForce FX5200 with the default drivers installed by Ubuntu (not sure how to check exactly what these are).
Trying to follow the guide in the HOWTO, when I get to this line:
*sudo nvidia-glx-config enable* I get this error:
```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```

The relevant section of my xorg.conf already reads:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

```

I don't know if 2d/3d hardware acceleration is activated or how to check. 
When I run glxgears I get no output to the command line.

I'm lost.

---

### Post by shinygerbil on 2005-11-03
try glxgears -printfps

Steve

---

### Post by pickarooney on 2005-11-03
cheers :)

3350 frames in 5.0 seconds = 669.902 FPS
3077 frames in 5.1 seconds = 607.997 FPS
2369 frames in 5.1 seconds = 463.259 FPS
2082 frames in 5.0 seconds = 415.891 FPS
2446 frames in 5.0 seconds = 489.014 FPS
2957 frames in 5.0 seconds = 591.155 FPS

Does that sound reasonable for an nVidia geforce fx5200 on an Athlon 1.2GHz machine with 760something megs of RAM? (I know that's extremely hard to estimate, but I don't know what ballpark figures I should be getting).

---

### Post by frodon on 2005-11-03
I have a AMD k7 700MHz, 512Mo SDRAM and like you a Geforce fx5200 and my fps is around 1300.
So i think your score is a bit low. do you you have this lines in the device section of your xorg.conf file ? : ```
Option          "RenderAccel"           "true"
```

---

### Post by pickarooney on 2005-11-03
No, the whole thing is just the five lines I posted above. 
Can I just add that in after the BusID line, restart X and test again?

---

### Post by frodon on 2005-11-03
Yes, you can, it's the good section.
It would be interesting to attach your xorg.conf in the next post if you still have problems with xorg configuration.

---

### Post by pickarooney on 2005-11-03
Ca marche!

6227 frames in 5.0 seconds = 1245.372 FPS
6994 frames in 5.0 seconds = 1398.796 FPS
7521 frames in 5.0 seconds = 1504.022 FPS
6522 frames in 5.2 seconds = 1258.245 FPS
3142 frames in 5.2 seconds = 599.769 FPS
7828 frames in 5.0 seconds = 1565.540 FPS
10268 frames in 5.0 seconds = 2053.539 FPS
9311 frames in 5.0 seconds = 1862.092 FPS
7459 frames in 5.0 seconds = 1491.745 FPS
7772 frames in 5.2 seconds = 1505.134 FPS
8801 frames in 5.0 seconds = 1760.106 FPS
10670 frames in 5.0 seconds = 2133.969 FPS
10828 frames in 5.0 seconds = 2165.468 FPS
10760 frames in 5.0 seconds = 2151.999 FPS
10792 frames in 5.0 seconds = 2158.322 FPS
10309 frames in 5.0 seconds = 2061.763 FPS
10705 frames in 5.0 seconds = 2140.939 FPS
11057 frames in 5.0 seconds = 2211.393 FPS
9421 frames in 5.0 seconds = 1883.981 FPS
7500 frames in 5.0 seconds = 1499.955 FPS

Thanks :)

---

