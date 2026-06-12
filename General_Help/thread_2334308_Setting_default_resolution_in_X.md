---
title: "Setting default resolution in X"
date: 2016-08-18
forum: General Help
---

### Post by Only1KW on 2016-08-18
I am currently running startx to start up a new instance of an X server in my fresh installation of Ubuntu 16.04.  I've used arandr to create and run an xrandr script to change my default resolution from 1024x768 to 1920x1080.  This script works perfectly when run manually from an xterm.  However, I want it to run automatically when X starts.  I've googled a ton and have seen a ton of suggestions, but none of them seem to work for me.  

I've added the command to my .xinitrc/.xsession/.xsessionrc/.xprofile/etc. files in my home directory.  I also tried adding it to /etc/X11/Xsession.d/45custom_xrandr-settings.  Nothing works.  If I redirect stdout and stderr of the xrandr command to a file, I get an empty file created.  Any ideas how I can do this?

---

### Post by Only1KW on 2016-08-19
I solved it.  I created the file /usr/share/X11/xorg.conf.d/10-monitor.conf and set it to the following:

```
Section "Monitor"        
        Identifier      "HDMI3"
        Option          "PreferredMode" "1920x1080"
        Option          "Position" "0 0"
EndSection
```

where "HDMI3" is the value of --output in my xrandr command, "1920x1080" the value of --mode, and "0 0" the value of --pos without the x in the middle.  I only have one screen, but I assume if you have dual-monitors, you would add multiple Monitor sections to that file.

---

