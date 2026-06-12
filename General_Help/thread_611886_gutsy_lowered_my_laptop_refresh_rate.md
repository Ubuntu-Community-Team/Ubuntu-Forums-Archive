---
title: "gutsy lowered my laptop refresh rate"
date: 2007-11-13
forum: General Help
---

### Post by bishop9226 on 2007-11-13
i had it at 60 in feisty but now the only option is 50hz under when i go to 'screen and graphics' in system settings.  im using a dell inspiron 6400/1540 intel

---

### Post by bishop9226 on 2007-11-13
oh and it came with an onboard nvidia card so im using the default nvidia drivers that load with gutsy

---

### Post by minus198 on 2007-11-13
Add this:

```
sudo nano /etc/X11/xorg.conf

add this to to the end section: "Screen"

Option          "metamodes" "1920x1200_60 +0+0
```

With your own screenresolution and refreshrate ofc.

Mine looks like this anyways:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        Option          "metamodes" "1920x1200_60 +0+0
EndSection

```

---

### Post by bishop9226 on 2007-11-13
this is mine with your line added in.  will this work?  or should i shorten mine to be like yours

> Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option          "metamodes" "1920x1200_60 +0+0
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

---

### Post by bishop9226 on 2007-11-13
bump

---

