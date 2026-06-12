---
title: "Screen resolution problems with HP M70 crt monitor (again)"
date: 2008-01-21
forum: General Help
---

### Post by YoungCthulhu on 2008-01-21
Gidday again...

Firstly, thanks go to **scxtt** :KS and **hashimoto** :KS for helping me set up my HP M70 crt  screen in the past!  I am having problems again as the only screen resolution available using System|Preferences|Screen Resolution is 800 x 600.  It was working great up to a week ago, about the time that I set up a separate user account for my daughter!  I can't see how this has affected things though.

Here is the relevant section of /etc/X11/xorg.conf:

> Section "Device"
        Identifier      "Gorts video card"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "Hewlett Packard M70"
#       Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Gorts video card"
        Monitor         "Hewlett Packard M70"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

I have tried lots of things; renaming the monitor under "Section "Monitor"", capitalising the video driver name from nvidia to NVIDIA, commenting out all of the ' Subsection "Display" options for all Depth values < > 24 but always end up with the X Window not loading.  

(On the positive side, this has forced me to start to use vim  :lolflag: ) .

Any ideas out there, or is it time to junk the old crt screen and get a nice new flat panel lcd one?  Problem is though that I use GIMP a lot and like the quality and colour that this old crt screen is capable of, it would just behave itself!

Cheers!

---

