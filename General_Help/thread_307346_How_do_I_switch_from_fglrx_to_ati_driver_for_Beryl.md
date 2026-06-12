---
title: "How do I switch from fglrx to ati driver for Beryl?"
date: 2006-11-26
forum: General Help
---

### Post by adds2one on 2006-11-26
Hello,

I am running a fresh install of Edgy and installed the fglrx driver by following the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I did this before I knew about Beryl.

I am pretty sure that my video card will work with Beryl because glxinfo | grep render

gives:

```
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic

```

Now I want to try and install Beryl and after much reading I think that I would like to go with AIGLX first. If that works for me, great, if not I can try with XGL.

My question is if I have installed the fglrx driver how can I switch back to the ati or radeon driver. Is it as simple as restoring my original xorg.conf file?

Here is my current xorg.conf:

```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection
```

and here is my old xorg.conf:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

```

Thanks so much for any help anyone can give me with this.

---

### Post by Dubbayoo on 2006-11-26
> **adds2one said:**
> Hello,

I am running a fresh install of Edgy and installed the fglrx driver by following the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I did this before I knew about Beryl.

I am pretty sure that my video card will work with Beryl because glxinfo | grep render

gives:

```
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic

```

Now I want to try and install Beryl and after much reading I think that I would like to go with AIGLX first. If that works for me, great, if not I can try with XGL.

My question is if I have installed the fglrx driver how can I switch back to the ati or radeon driver. Is it as simple as restoring my original xorg.conf file?

I believe it is. You might try just replacing fglrx with ati in the current config.

---

### Post by adds2one on 2006-11-26
I just tried using my old xorg.conf file (the default one using the ati driver) and now when I type glxinfo | grep render I get:

```

direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL

```

I guess this means that I cannot use Beryl with AIGLX with this ati driver. I will give the radeon one a try.

---

### Post by adds2one on 2006-11-26
I tried the radeon driver and I get the exact same output from glxinfo | grep render:

```
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL

```

Does this mean that I have to use fglrx drivers and XGL?

I am confused as according to many HOW-TOs I have read the radeon driver should work with my card to get Beryl working with AIGLX.

Do I not need direct rendering to say YES?

---

### Post by slicky on 2006-11-26
hi.. i have the same problem.. but with a ATI radeon 9600.. iv got the fglrx drivers and when i run glxinfo:

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0

direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9600 XT Generic

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6011 (8.28.8)

and this means.. that my DRI is disable.. and it uses 3d acceleration instead (i think)

check your cpu usage, mine is like 40-70% all the time.. 

this is my xorg.conf

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option "RenderAccel" "True"
EndSection


then i found this:
[http://ubuntuforums.org/showthread.php?t=199835](http://ubuntuforums.org/showthread.php?t=199835)

that says that it&#347; normal for the dri to not be enable..

but i wonder why the cpu usage are so high..


> 
Does this mean that I have to use fglrx drivers and XGL?

well, if it works.. run with it

maby this one can be interesting to:
[http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

---

### Post by adds2one on 2006-11-27
OK, got mine to work. 

I had to uninstall fglrx via synaptic and then I changed my xorg.conf to this:

```
Section "Device"
Identifier "{your card model}" <-do not edit this line in your xorg.conf
Driver "radeon"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
## Some may experience very poor performance without hashing the following line.
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
Option "AGPFastWrite" "on"
BusID "whatever yours is"
EndSection
```

I also added this which made things smoother:

```
Option          "TripleBuffer" "true"
```

Slicky, I am not sure but I think it is a problem that your xorg.conf doesn't show the name of your specific video card. Maybe you need to reconfigure xorg and select your card in the process. Can't remember the command to reconfigure xorg but if you do a quick search of the forum you will find the answer.

---

### Post by misha680 on 2006-12-07
I would personally advise sticking with fglrx/Xgl, because unfortunately radeon+aiglx on mobility radeon 9000 is slooow compared to fglrx/Xgl. There are some crashes, but there are two changes you can make to get rid of most if not all of them ([http://ubuntuforums.org/showthread.php?p=1854472&posted=1#post1854472)](http://ubuntuforums.org/showthread.php?p=1854472&posted=1#post1854472)).
I wish the open source drivers worked better for 3d on this card :( (well faster anyway).

Misha

---

