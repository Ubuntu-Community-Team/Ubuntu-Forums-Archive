---
title: "NX closes when I scroll with the third mouse button on my thinkpad"
date: 2008-05-15
forum: General Help
---

### Post by Mortuis on 2008-05-15
As the title says, when I start an NX session it works fine.  When I try to scroll down in firefox by holding the third mouse button on my thinkpad T20 and pushing down on the trackpoint the NX session closes abruptly and I receive a message telling me to check my connection.

The following is my mouse entry in /etc/X11/xorg.conf that enables my third mouse button to scroll in this way.

> 
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
       Option      "EmulateWheel"        "on"
       Option      "EmulateWheelButton"  "2"
EndSection


---

### Post by Mortuis on 2008-05-17
I finally got my hands on the server, apparently the problem had to do with this url: [http://developer.pidgin.im/ticket/4986](http://developer.pidgin.im/ticket/4986)

For whatever reason, when the server computer tries to scroll down on that page, X restarts.  That must have been what was kicking me off NX.

---

