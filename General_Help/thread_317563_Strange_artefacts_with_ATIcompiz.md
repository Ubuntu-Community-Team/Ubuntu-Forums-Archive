---
title: "Strange artefacts with ATI/compiz"
date: 2006-12-12
forum: General Help
---

### Post by freshi on 2006-12-12
hi,

i've got some problems with the open source ati driver and compiz.

First off, some facts:

```
freshi@keie:~$ dpkg -l|grep compiz
ii  compiz-freedesktop               0.3.4-0gandalfn1                     OpenGL composition manager
ii  compiz-freedesktop-extra         0.3.4.2-0gandalfn1                   Animation plugin for compiz
ii  compiz-freedesktop-gnome         0.3.4-0gandalfn1                     Gnome window decorator and libraries for Com
ii  gnome-compiz-manager             0.9.14-1gandalfn1                    Compiz Gnome Manager
ii  gnome-compiz-manager-extra       0.1.5-0gandalfn1                     Compiz Gnome Manager Extra
ii  libgnome-compiz-manager          0.9.14-1gandalfn1                    Compiz Gnome Manager
```

ATI driver is the official one from the edgy repos. But I've played around with fglrx, so here's the glxinfo stuff:

```
freshi@keie:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
```

And that's the relevant xorg.conf part:

```
Section "Module"
        Load    "bitmap"
        Load    "dbe"
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
        Identifier      "Standardgrafikkarte"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AGPFastWrite" "yes"
        Option          "AGPMode" "8"
        Option          "ColorTiling" "on"
        Option          "EnablePageFlip" "true"
        Option          "AccelMethod" "EXA" # alt: XAA
        Option          "EXANoOffScreenPixMaps"
        Option          "DRI" "true"
        Option          "RenderAccel" "true"
        Option          "backingstore" "true"
#       Option          "mtrr" "on" #
#       Option          "DisplayPriority" "HIGH" #
#       Option          "DPMS"  #
#       Option "AllowGLXWithComposite" "true"
#       Option "SubPixelOrder" "NONE"
#       Option "DynamicClocks" "true"
#       Option "UseFBDev" "true"
#       Option "AGPSize" "128"
EndSection
```

Everythings fine, performance is sometimes a little bit slow, but this seems to be ok on my machine.

The question is, how can I get rid off this ugly desktop background artefacts as shown in the screenshots below? Any suggestions?

[http://www.andialbrecht.de/apache2-default/Bildschirmfoto.png]("http://www.andialbrecht.de/apache2-default/Bildschirmfoto.png")
[http://www.andialbrecht.de/apache2-default/Bildschirmfoto-1.png]("http://www.andialbrecht.de/apache2-default/Bildschirmfoto-1.png")

---

