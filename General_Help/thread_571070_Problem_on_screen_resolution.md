---
title: "Problem on screen resolution"
date: 2007-10-08
forum: General Help
---

### Post by satimis on 2007-10-08
Hi folks,


Ubuntu 7.04 server amd64
Display - Philips BrilliAnce 200WP
ASUS vedio card with Nvidia chip set


On running;
$ xrandr```

 SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 325mm x 260mm )  *61  
 1   1024 x 768    ( 325mm x 260mm )   61  
 2    800 x 600    ( 325mm x 260mm )   61  
 3    640 x 480    ( 325mm x 260mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

```

The current screen resolution is "1280 x 1024   ( 325mm x 260mm )  *61"

$ cat /etc/X11/xorg.conf```

......
 Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1280x1024" "1024x768"
        EndSubSection
EndSection
....

```

The display and vedio card can support "1680x1024" resolution.

Whether I need to download and install the Nvidia driver on nvidia.com?  TIA.


B.R.
satimis

---

