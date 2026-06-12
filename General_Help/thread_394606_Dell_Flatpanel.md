---
title: "Dell Flatpanel"
date: 2007-03-27
forum: General Help
---

### Post by quake120 on 2007-03-27
I just bought a 2407FPW (24" Dell Widescreen monitor) and have been unable to configure it to display its native resolution of 1920x1200. 
I'm using an Intel 845 MB w/ the 810 graphics chipset. I do have the drivers installed for the card. I am using Edgy w/ both Gnome and KDE installed.  

I've already tried "sudo dpkg-reconfigure xserver-xorg". It has the correct resolution listed, but after I restart X (either by CTRL+ALT+BACKSPACE or rebooting) it reverts to something really low like 640x480. I tried manually editing xorg.conf but it never did anything to help. I've messed around with the system config tool in KDE but it never keeps the resolution either.
Any suggestions? Anybody have this monitor/chipset combo that is actually working?

---

### Post by acormack on 2007-03-28
I had  a lot of problems getting my LG L194WT to work at its correct resolution 1440 x 900 on Kubuntu 6.10

In the end I manually edited the /etc/X1/xorg.conf to set the monitor section to the correct values (which I found in the user manual)

Then I just added an extra line in the Screen Section for the correct resolution.

It took a lot of playing aroung but it worked perfectly in the end (and touch wood has been fine since) - although only with a DefaultDepth of 24 not 32.

Just in case it is useful here are extracts from my file.  You will need to substitute values specific to your flat panel:

{snip}

Section "Monitor"
[B]    Identifier     "Monitor0"
    VendorName     "LG"
    ModelName      "L194WT"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
[/B]EndSection

{snip}

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       **24**
        Modes      "1600x1200" **"1440x900"** "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

{snip}


Hope this helps


Alec

---

