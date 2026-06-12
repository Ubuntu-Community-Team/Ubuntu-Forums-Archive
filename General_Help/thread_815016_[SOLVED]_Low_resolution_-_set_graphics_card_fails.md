---
title: "[SOLVED] Low resolution - set graphics card fails"
date: 2008-06-01
forum: General Help
---

### Post by Kevbert on 2008-06-01
I recently decided to install Xubuntu on an old PC.  The specs are as follows:
Monitor - LG RZ-15LA70 LCD TV monitor
Display card - 3dfx Voodoo Banshee 16Mb
RAM - 512Mb PC100
CPU - Athlon 900
HD - 40Gb IDE
I'm having a few teething problems setting up the graphics card.  My xorg.conf file displayed 'Configured Monitor' and 'Configured Video Device' and nothing else under each section.  The display would not go to any resolution above 800x600.  I've looked at the [Community Document]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541") and tried to set up the xorg.conf file to get higher resolutions.  My problem is that I can set up the Monitor settings as follows:
```
Section "Monitor"
        Identifier    "LG RZ-15LA70"
        HorizSync     60
        VertRefresh   75
EndSection
```
but I can't set up the video 'Device' modes.  As soon as I set a mode such as 
```
Section "Device"
        Identifier    "Voodoo Banshee"
        Depth         24
        Modes         "1024x768"
EndSection
```
the PC cannot set the resolution on reboot and goes into low graphics mode.
I cannot get the display to reconfigure using the 'dpkg-reconfigure...' command or by using autoconfigure - the display reverts to 800x600 max.  If I leave the 'Device' as 'Configured Video Device' only (nothing else in section) then the display goes to 1024x768 (by the look of it).  The settings only show 'Default' for the resolution in Settings Manager - Display Preferences.
The monitor (specified) will go from 640x480 to 1024x768.  The display card (specified) will go from 320x200 to 1600x1200 in 256, 64K, 16 million colours(yet its only 16Mb ?).
What's the colour depth for 16 million colours ?
If I enter the resolutions as shown in the Community document with HSync and VSync, how do I know what's - and + as nothing in the manuals shows this ?

---

### Post by Kevbert on 2008-07-25
bump.

---

### Post by mali2297 on 2008-07-25
I think you need to specify the driver, [tdfx]("http://linux.die.net/man/4/tdfx") seems suitable. Furthermore, Depth and Mode should probably be put in the Screen section.

Try something like
```

Section "Device"
        Identifier    "Voodoo Banshee"
        Driver        "tdfx"
EndSection

Section "Monitor"
        Identifier    "LG RZ-15LA70"
        HorizSync     60
        VertRefresh   75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Voodoo Banshee"
        Monitor         "LG RZ-15LA70"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        # Here you should also specify input devices
EndSection

```

Also, see this thread:
[http://ubuntuforums.org/showthread.php?t=18106](http://ubuntuforums.org/showthread.php?t=18106)

---

### Post by Kevbert on 2008-07-26
Thanks for replying.  I've just tried the changes you suggested.  It seems that regardless of including the driver, and adding screen modes and colour depths I still can only use the default setting and 512x384@75Hz (where did that come from ?).  These two settings are displayed by Xfce Settings Manager - Display Preferences.  Each time I made a change, saved the file and rebooted.  It's very puzzling... but thanks again anyway.

---

### Post by Kevbert on 2008-08-11
Seeing as no-one can help, I'll just have to put up with this restriction and close this thread.

---

