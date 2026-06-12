---
title: "X3500 no direct rendering"
date: 2008-04-18
forum: General Help
---

### Post by gus_zernial on 2008-04-18
I have an Asus P5E-VM HDMI motherboard with Intel X3500 GMA, running Kubuntu
7.10 with 2.6.22-14-generic kernel. I compiled and installed latest drm and mesa
from sources, and then compiled and installed xf86-video-intel 2.2.99.902, but cannot
get 3D and direct rendering to work.  Some info below - I can post more if needed ...

Should this work? Am I doing something wrong? Ideas to diagnose and/or fix?

$ glxinfo
.....
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.1
(etc)

$ cat Xorg.0.log | grep EE

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/i965_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

$lsmod  (partial)

i915                        55852  1
drm                        155432  2 i915
intel_agp               25620  1
agpgart                 35016  3 drm,intel_agp

$ cat /etc/X11/xorg.conf (partial)

.
.
Section "Module"
       Load "glx"
       Load "dri"
EndSection

Section "Device"
       Identifier      "Intel Corporation 965 G1 Integrated Graphics Controller"
       Driver          "intel"
       BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
       Identifier      "CPD-G520"
       Option          "DPMS"
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Device          "Intel Corporation 965 G1 Integrated Graphics Controller"
       Monitor         "CPD-G520"
       DefaultDepth    24
       SubSection "Display"
               Modes           "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
       EndSubSection
EndSection

Section "ServerLayout"
       Identifier      "Default Layout"
       Screen          "Default Screen"
       InputDevice     "Generic Keyboard"
       InputDevice     "Configured Mouse"

EndSection

Section "dri"
       Mode    0666
EndSection

---

### Post by -Zeus- on 2008-04-21
why don't you try

```
LIBGL_DEBUG=verbose; glxinfo
```

---

### Post by sippnonacorona on 2008-05-18
This mainboard uses the Intel G35/X3500 chipset. There is no HARDY 8.04 support for this yet, is there?

Are you trying to use the Intel i915 driver on the G35? Did you get it to work?

Right now, I'm using the VESA VGA=795 setting in the grub file at boot time to get a desktop that is stable. I'd love to be able to use the full feature set of this video if possible.

---

