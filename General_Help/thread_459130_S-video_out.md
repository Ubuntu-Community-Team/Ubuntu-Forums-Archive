---
title: "S-video out"
date: 2007-05-30
forum: General Help
---

### Post by shiznatix on 2007-05-30
Hello,

I have been trying to get my svideo out to work to no avail. I have heard success stories from people who have edited their xorg.conf file but I have not had any success. In my defense I don't really know anything about the file or how to configure it.

The computer I am using is a compaw presario v5000 series and the video situation is this:

> 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)


and my xorg.conf file looks like this:

> 
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection


that is the relivant sections of both outputs. If anyone can help me out I would be very appreciative.

---

### Post by snifer on 2007-06-01
you can try this: [http://ubuntuforums.org/showthread.php?p=2512390](http://ubuntuforums.org/showthread.php?p=2512390)

---

