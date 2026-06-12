---
title: "middle mouse button in thinkpad doen't work properly."
date: 2007-02-05
forum: General Help
---

### Post by jeangleur on 2007-02-05
Hello,

I am using an ibm thinkpad T30 with those funny middle mouse buttons. It works in firefox but not in the rest of ubuntu. how do I configure it in the right way?

Thanks, 

Jean - [www.ruuudi.de](www.ruuudi.de)

---

### Post by ubu fubar on 2007-02-05
If you mean the [UltraNav]("http://www.thinkwiki.org/wiki/UltraNav") thingy, here's the relevant section of my xorg.conf from my T30. Maybe it's of some use to you:

-----------------------------------------------

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
        Option          "EmulateWheel"          "true"
        Option          "EmulateWheelButton"    "2"
EndSection

-----------------------------------------------

How do you want to use the buttons anyway? Do the other UltraNav buttons work (left & right click for example)?

---

