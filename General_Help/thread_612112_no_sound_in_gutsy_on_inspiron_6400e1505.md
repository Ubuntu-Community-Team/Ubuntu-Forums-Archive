---
title: "no sound in gutsy on inspiron 6400/e1505"
date: 2007-11-13
forum: General Help
---

### Post by bishop9226 on 2007-11-13
anyone have a fix?  

when i click on the volume control on the taskbar it says

No volume control GStreamer plugins and/or devices found

i also have only a generic monitor and am stuck at 50hz

here

```
art@art-laptop:~$ lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```

for the video...

```
Section "Screen"
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
```

---

### Post by Paul S on 2007-11-20
Works fine here on E1505 with same sound card.  Are you sure you installed all of gutsy?  Try "sudo aptitude install ubuntu-desktop" in a terminal to confirm it.

For the nvidia card, make sure you're using the restricted drivers to get the full capability of that card.  Then you can use "nvidia-settings" to make changes.

Also, be aware of this bug [http://ubuntuforums.org/showthread.php?p=3806971#post3806971](http://ubuntuforums.org/showthread.php?p=3806971#post3806971) on your nvidia driver.  You should install the 169.04 beta from nvidia.com site.

HTH

---

