---
title: "Noob question..."
date: 2007-06-19
forum: General Help
---

### Post by kdarkentity on 2007-06-19
how do i change my color depth to 16 bit????

---

### Post by kuja on 2007-06-19
You should be able to do that in your /etc/X11/xorg.conf file

Look for a line like this:
> 
Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    **DefaultDepth    24**
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Assuming there is a subsection below with depth set to 16, just change the DefaultDepth line to "16"

If a subsection like that doesn't exist, it will be identical to your other one(s), just the depth will say something else (ie 8/16/24/etc)

---

