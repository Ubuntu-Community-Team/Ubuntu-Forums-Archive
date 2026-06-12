---
title: "Blue tint when using TV out on nVidia 6200"
date: 2007-08-04
forum: General Help
---

### Post by visionviper on 2007-08-04
I have fixed this before, but I remember it took me a couple weeks of searching to find the answer. I remember it had to do with editing the xorg.conf file. So here is what mine has:

```

Section "Device"
        Identifier      "nVidia Corporation NV44A [GeForce 6200]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Q7b"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV44A [GeForce 6200]"
        Monitor         "Q7b"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1152x864"      "1024x768"     $
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x1024"     "1152x864"      "1024x768"     $
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x1024"     "1152x864"      "1024x768"     $
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x1024"     "1152x864"      "1024x768"     $
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x1024"     "1152x864"      "1024x768"     $
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1152x864"      "1024x768"     $
        EndSubSection
EndSection

```

That is what I have in relation to video and whatnot. I know I need to make some changes. The "Q7b" is the LCD monitor I used to set up ubuntu and install mythtv. Now I need to, I am guessing, add a new screen - my crt television. I don't know how to do that and maybe someone could point me in the right direction and clarify exactly what I need to do.

I have the latest nVidia drivers installed.

---

### Post by Gokee2 on 2008-05-08
Every get this fixed?  If so how?

Thanks

---

