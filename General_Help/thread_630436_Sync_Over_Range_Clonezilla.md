---
title: "Sync Over Range Clonezilla"
date: 2007-12-03
forum: General Help
---

### Post by Gotit on 2007-12-03
I have a problem where I get Sync Over Range when trying to boot Clonezilla from a CD.  It seems to start out OK as I see text scroll by and i can select defaults.  But then it comes time to display the GUI (at least I think that what it's doing) and I get a black screen with Sync Over Range.

It seems my config is OK as /etc/X11/xorg.conf shows:
> Section "Monitor"
        Identifier      "VT988"
        Option          "DPMS"
        Horizsync       28-64
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "VT988"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1024x768"      "832x624"      "800x600"        "720x400"       "640x480"
        EndSubSection


What can I do to resolve this so I can see the GUI?

---

