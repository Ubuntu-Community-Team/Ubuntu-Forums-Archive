---
title: "Non-existant Monitor Detected in Screen Resolution settings"
date: 2008-05-08
forum: General Help
---

### Post by tomburns on 2008-05-08
Hey all, I've attached a screenshot of the Screen Resolution settings window sine i'm not sure how else to explain what's going on. It looks like ubuntu has decided that i have a phantom monitor. This is causing rendering issues with certain compiz effects, like the Win+Tab window switching one and the "enter your password" sudo dialog for admin actions. Where should i be looking for the source of this issue?

---

### Post by Achtung on 2008-05-08
How about disabling the second monitor? Click System/Administration/Screens and graphics to bring up the correct dialog.

---

### Post by tomburns on 2008-05-08
> **Achtung said:**
> How about disabling the second monitor? Click System/Administration/Screens and graphics to bring up the correct dialog.

Hmm, I don't seem to have anything called Screens and Graphics under System/Administration. I'm in Hoary, does that change where i should be looking?

---

### Post by chrisccoulson on 2008-05-08
Screens and Graphics is deprecated. Could you post your /etc/X11/xorg.conf?

---

### Post by tomburns on 2008-05-08
Here are the non-InputDevice sections:

```

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection


```

---

