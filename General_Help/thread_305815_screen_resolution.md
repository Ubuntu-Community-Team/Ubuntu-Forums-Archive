---
title: "screen resolution"
date: 2006-11-24
forum: General Help
---

### Post by Stochastic on 2006-11-24
Hey I'm trying to increase my screen resolution, I've run ```
sudo dpkg-reconfigure xserver-xorg
``` and it gave me larger resolution choices up to 1900x1200kinda size(I forget the actual number) and I selected the default to be that but upon reboot of the xserver (ctrl+alt+backspace) nothing changes and the screen resolution setting in the gnome menu does not show any options above 1280x768 here's the important section of my xorg.conf file: ```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-96
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854"  "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "64 0x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854"  "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "64 0x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854"  "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "64 0x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854"  "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "64 0x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854"  "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "64 0x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854"  "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "64 0x480"
        EndSubSection
EndSection

```

any suggestions?

---

### Post by futz on 2006-11-24
The critical part to get the results you want is this:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-96
        VertRefresh     43-60
EndSection
```

Look up the specs for your monitor and plug in the correct numbers for HorizSync and VertRefresh. Then restart X by hitting CTRL-ALT-BACKSPACE.

In monitor specs you may find HorizSync referred to as Fh (or similar) and VertRefresh as Fv (or similar). Whatever. What you need is the correct numbers.

---

### Post by Stochastic on 2006-11-24
I'm running a laptop, how do I figure out what type of monitor I have?

---

### Post by futz on 2006-11-24
> **Stochastic said:**
> I'm running a laptop, how do I figure out what type of monitor I have?
In that case those numbers don't look so far fetched. 

I run a 19" LCD and my HorizSync is 30-65 and my VertRefresh is 50-75, but it runs at 1280x1024 native. Judging by that and all the other xorg.conf files I've played with (a lot), your numbers look fairly reasonable. But if it isn't working, then they can't be right unless there's something I don't know about (impossible! :shock: ;) )

Can you look up some specs for the lappy that might have that info in it?

Alternately you could google for a modeline generator and have it build you one for your desired resolution and vert refresh rate (likely 60Hz for LCD panel).

---

### Post by fragos on 2006-11-24
Never use a resoltion that exceeds the specs for your monitor.  Regardless of what resolutions you've placed in xorg.conf the display driver used will be the final arbitor of whats useable.  When you run dpkg-reconfigure xserver-xorg it will change the driver selected in xorg.conf to an open source 2D driver which may not support the same resolutions as ATI's 3D driver.  If you've never installed an ATI driver, do so.  If you have, edit /etc/X11/xorg.conf to call out the 3D driver name.

---

