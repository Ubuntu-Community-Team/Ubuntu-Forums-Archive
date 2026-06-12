---
title: "Color Bit Depth?"
date: 2007-06-19
forum: General Help
---

### Post by cmillican on 2007-06-19
ManiaDrive runs extremely slow (1-2 fps) on my computer, so I want to change the bit depth to 16 to speed things up. I was wondering how I could do that. 

Thanks,
Chris

---

### Post by mikewhatever on 2007-06-19
Type the following in the terminal
> gksudo gedit /etc/X11/xorg.conf
Scroll down to the resolution section and edit the default depth, but make sure it has a section to match to.
> Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [GeForce Go 7400]"
    Monitor        "Generic Monitor"
    DefaultDepth    [COLOR="DarkRed"]16[/COLOR]
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       [COLOR="DarkRed"]16[/COLOR]
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection

---

