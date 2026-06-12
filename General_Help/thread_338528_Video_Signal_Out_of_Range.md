---
title: "Video Signal Out of Range"
date: 2007-01-14
forum: General Help
---

### Post by greatwhitenortherner on 2007-01-14
I've re-installed Ubuntu Edgy.  When Ubuntu boots instead of the Ubuntu graphic being displayed, my monitor displays "SIGNAL OUT OF RANGE".  When it gets to GDM, all is normal.  I enter the username and password and go into GNOME.  Same thing happens when I shut down the computer.  Instead of getting the shutdown screen, the video signal goes out of range again.  Strange thing is, I used to get the Ubuntu startup and shutdown screens.  What might be wrong, and how can I fix it?  I can live with the way things are, but I'd like to have things working properly if that's possible.

Thanks

---

### Post by kebes on 2007-01-14
I'm guessing that your file "/etc/X11/xorg.conf" is missing a simple display mode like "800x600" or "640x480" which is what the bootup/shutdown screens probably use. If you really want to fix this, you can post your xorg.conf here and someone will probably be able to spot the problem.

You can look into your xorg.conf and see if the "Screen" Section has the right display modes listed.

EDIT: For example, a normal screen section might look like this:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Default Card"
        Monitor         "DELL 2007FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection


```

Notice that the lines with "Modes" have "800x600" and other low-resolution modes enabled.

---

### Post by msimon1960 on 2007-01-16
Same problem with Ubuntu and Kubuntu 6.10.  Worked fine in 6.06.

I checked the file you mentioned and sure enough -- it's completely empty.

Can the file be replace or recreated?

---

### Post by Tux Aubrey on 2007-01-16
I may be wrong (and please correct me if I am), but isn't this problem happening before X starts - so why would xorg.conf be the source of the problem?  And why would msimon1960's xorg.conf be "completely empty" ?  Surely there would be the default stuff there on a new install?

If its a splash screen problem (and exit), I would have thought that grub hasn't detected the screen res properly.  See this  [thread ]("http://ubuntuforums.org/showthread.php?p=2012969#post2012969")for a suggested way to fix it.

Also, I'd suggest that if you are playing around with xorg.conf, you make a backup first (still can't believe its empty and yet you get past logon OK)

---

### Post by msimon1960 on 2007-01-20
Just to confirm -- I've reloaded version 6.10 from scratch and the xorg.conf file is empty -- nada -- nothing.  When starting / exiting the system just hangs for a bit (30-40 seconds) with the message 'out of range' before moving on.

I then loaded 6.06 from scratch (same machine) and it created the file just fine.

I take it that GRUB passes the video parameters to 6.06/6.10 to create the xorg.conf file?  If so, it doesn't appear that 6.10 is getting the message.

Matt.

---

