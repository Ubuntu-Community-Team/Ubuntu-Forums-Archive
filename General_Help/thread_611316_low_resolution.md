---
title: "low resolution"
date: 2007-11-12
forum: General Help
---

### Post by odindio on 2007-11-12
I've got a system that keeps popping back to low resolution 6xx x 4xx.

I've reconfigured -xorg several times and this no longer works.  It's an Amd system with a trident blade 3D on board video. Is there a fix for me?

Update! I decided to give sudo dpkg-reconfigure -phigh xserver-xorg another try.  It hasn't worked the last 3 or more times I tried it.  It worked for now.  Very strange!  What could be going on here?  I'm not sure if I'll have that resolution the next time I restart.  I restarted and lost it.  I ran that reconfig and got it back.  ?????????????

Here is a section of -xorg

Section "Device"
        Identifier      "Trident Microsystems CyberBlade/i1"
        Driver          "trident"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Acer 77e"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Trident Microsystems CyberBlade/i1"
        Monitor         "Acer 77e"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by NT4usB on 2007-11-12
Looks like that card/video is a problem child. Lots of issues posted, few solutions.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-trident/+bug/57862](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-trident/+bug/57862)
[more]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+%22Trident+Microsystems+CyberBlade%2Fi1%22&btnG=Search")

one suggested solution:
```
Section "Device"
        Identifier "Trident Microsystems CyberBlade XP4m32"
        Driver "trident"
        BusID "PCI:1:0:0"
       [b] Option "AccelMethod" "EXA"
        Option "ShadowFB" "false"[/b]
EndSection
```

another suggestion was use vesa instead of trident for the driver.

---

