---
title: "Installing Video Driver Help, am I doing this right?"
date: 2007-06-13
forum: General Help
---

### Post by Citizin on 2007-06-13
Alright, after installing Ubuntu endless times, Im going to type out step by step how I setup my drivers and computer, maybe its ME thats doing something wrong.


The FX 5700LE is plugged a PCI Slot
The Intel Integrated is the default right now

Right now, im trying yet again to get my video card to work. For some reason whenever my FX5700LE is hooked up, a LIVE CD, or off the HDD it just wont boot, it freeze while the progress bar is moving. Recovery mode is the same way. Thats when I have the card enabled in the BIOS, NOT using my integrated.

When I used my integrated, everything works like cake.

Now, if the only way I can get nvidia drivers installed is by using my integrated, then I have to. So I just installed the drivers in the restricted drivers app in ubuntu (**NOTE: I have used ENVY, and other tools for installed nvidia drivers, the same thing happens regardless)**.

So, im on my integrated, installed the drivers, this is what my xorg.conf file reads.

```
Section "Device"
    Identifier    "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    Driver        "nvidia"
    Busid        "PCI:0:2:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "COMPAQ FS760"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    Monitor        "COMPAQ FS760"
    Defaultdepth    24
    SubSection "Display"
        Depth    1
        Modes        "1152x864"    "1024x768"    "800x600"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    4
        Modes        "1152x864"    "1024x768"    "800x600"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    8
        Modes        "1152x864"    "1024x768"    "800x600"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    15
        Modes        "1152x864"    "1024x768"    "800x600"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    16
        Modes        "1152x864"    "1024x768"    "800x600"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    24
        Modes        "1152x864"    "1024x768"    "800x600"    "640x480"
    EndSubSection
EndSection
```

Also, LSPCI brings the following for my nvidia card.
(That dosn't look like a busid to me)

[B]01:0a.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)


[/B]So, am I doing this correctly, I know when I restart my ubuntu will NOT come back on :( But Hey, try and try again.

It really makes me mad that ubuntu is in the 7.04 stable release stage and it won't even work with my video card.

---

### Post by Damanther on 2007-06-15
You might try the nv driver instead of the nvidia.

It seems to work better.

Mike

---

### Post by Citizin on 2007-06-15
I tried that in dpkg-reconfigure -phigh xserver-xorg and it just gave me the same results, ubuntu pauses at the loading bar about 10-15% in.

---

### Post by Crafty Kisses on 2007-06-16
> **Citizin said:**
> I tried that in dpkg-reconfigure -phigh xserver-xorg and it just gave me the same results, ubuntu pauses at the loading bar about 10-15% in.

You can try using Envy, that automatically installs the NVIDIA drivers.

---

### Post by strabes on 2007-06-16
Why don't you just install using the alternate CD?

---

### Post by Citizin on 2007-06-16
I tried envy, I tried the alternate CD, I tried lots of things, none of them work, it just fails to work with my video card.
 
Maybe in Ubuntu's next release Ill download it and try again, but I like how XP only takes 5 minutes to install with my video card.
 
Thanks for trying guys.

---

