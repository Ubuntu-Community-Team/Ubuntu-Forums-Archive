---
title: "OpenGL using Mesa instead of Ati"
date: 2007-03-02
forum: General Help
---

### Post by Naatan on 2007-03-02
Hi, so far I've had a lot of trouble getting my video card working decently, as it is everything is working fine except for opengl, because of this I can't use MetaCity, which sucks.

I have an Ati Radeon x1600 which is kinda new and not well supported by linux, but hey I got it working mostly.

When I type fglrxinfo in terminal I get the following:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

Notice the "**Xlib:  extension "XFree86-DRI" missing on display ":0.0".**"

Any idea what is causing this?

My display settings in xorg.conf look like this:

```

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. ATI Default Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection
```

Thank in advance to who ever can help me :)

---

### Post by Naatan on 2007-03-02
bump

---

### Post by Ramses de Norre on 2007-03-02
Is fglrx in /etc/modules?

---

### Post by Maestro23 on 2007-03-02
I have an ATI Radeon X1600 as well.  I used the following guide for my card: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I used Method 1 to install the fglrx driver.

Good luck.

---

### Post by Naatan on 2007-03-02
Thanks for your replies, 

@Ramses de Norre: /etc/modules contains the following:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
```

So no fglrx.. can I just add that myself?

@Maestro23, I've tried both methods before aswell as other, but no matter what I try, mesa is always the opengl driver :(

---

### Post by Naatan on 2007-03-02
cool! I placed fglrx in /etc/modules and restarted x, now fglrxinfo returns:

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6334 (8.34.8)
```

Only now I can't use Beryl anymore, as it returns:

```
$ beryl-xgl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl-xgl: No composite extension
```

This is because of the following section in xorg.conf:

```
Section "Extensions"
        Option     "Composite" "Disabled"
EndSection
```

I tried changing this to Enabled, but then the GL driver is Mesa again..

anyone know how to get these two working together?

---

### Post by Naatan on 2007-03-02
bump

---

### Post by warjowuch on 2007-03-02
fglrx does not support compositing. You'd have to install XGL or NOT use fglrx but the opensource driver instead. Hope you can switch back to it, I have a whole lot of troubles for this...

---

