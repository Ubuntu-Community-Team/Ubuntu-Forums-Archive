---
title: "BusId for video card"
date: 2007-01-06
forum: General Help
---

### Post by rbhigday on 2007-01-06
How do I find the busId for my ati radeon x700?

---

### Post by taurus on 2007-01-06
```
lspci
```

---

### Post by RandomJoe on 2007-01-06
Expanding a tad - run 'lspci' in a terminal, and find the line that is your video card.  In my case, it looks like this:

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0392 (rev a1)

The Bus ID is the last three sets of numbers, or from the above line I would get:

BusID "PCI:1:0:0"

---

### Post by rbhigday on 2007-01-06
Ok thanks for that help, I did that and I get this:

01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700]

Thus my busId is 01.00.0 for my primary, but my secondary was not listed how would I find that?

I am amazed at the amount of info some of you know, to someday be at that level is my goal.

---

### Post by taurus on 2007-01-06
Is the second one an onboard or a PCI/AGP card?  I bet the other one would be 02:00:00!!!

---

### Post by rbhigday on 2007-01-06
> **taurus said:**
> Is the second one an onboard or a PCI/AGP card?  I bet the other one would be 02:00:00!!!

No the secondary is the second video port on X700.

I currently have two monitors connect to that card and both show the same exact thing, trying to get the busid for both to setup xorg.conf for dual monitiors and I have noticed that the others all had busid for both video ports.

---

### Post by taurus on 2007-01-06
So you have one video card but two connections on the back, right!  Then, I believe there is only one BusID...

---

### Post by RandomJoe on 2007-01-06
If you have a dual-head card (both outputs on a single card/GPU) then you will use the same Bus ID for both "cards".  But you add a Screen line to indicate which port (0 or 1) that "card" is.  Following is the relevant section for my dual-head nVidia setup.  (I should say, I assume ATI works the same way, I haven't used a dual-head ATI!)

My second monitor is a projector, so it has wierd modelines.  Normal monitors shouldn't need that...

```
Section "Device"
        Identifier      "nVidia0"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo" "false"
        Screen          0
EndSection

Section "Device"
        Identifier      "nVidia1"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo" "false"
        Screen          1
EndSection


Section "Monitor"
        Identifier      "SyncMaster1"
        Option          "DPMS"
EndSection

Section "Modes"
        Identifier      "Modes2"
        ModeLine        "852x480" 33.1 852 872 912 1068 480 483 488 516 -hsync -vsync
        ModeLine        "720x480" 26.7 720 736 808 896 480 481 484 497
EndSection

Section "Monitor"
        Identifier      "SyncMaster2"
        UseModes        "Modes2"
        HorizSync       25-68
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "screen0"
        Device          "nVidia0"
        Monitor         "SyncMaster1"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "nVidia1"
        Monitor         "SyncMaster2"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes "852x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Dual Screens"
        Screen          0 "screen0"
        Screen          1 "screen1" rightof "screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

---

