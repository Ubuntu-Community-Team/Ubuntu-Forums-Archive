---
title: "lost ability to scroll after upgrade to 8.04"
date: 2008-04-26
forum: General Help
---

### Post by Fittersman on 2008-04-26
i just upgraded to the new ubuntu 8.04 from 7.10 (did a fresh install) but now scrolling is broken. Only a few applications can actually scroll properly (envy is the only one that i remember being able to scroll), most cannot scroll such as firefox, nautilus, etc. Any ideas how to make scrolling work again?

this is the relevant part of my xorg.conf file
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection


```

---

### Post by Fittersman on 2008-04-26
alright, i got the scroll wheel working but there is another problem...

while in firefox if i spin the scroll wheel quickly, firefox cannot keep up so it keeps scrolling long after i have stopped the wheel. That is probably a bit confusing, so ill use an example. Lets say firefox can scroll at 2 pages/second, but i spun the scroll wheel at 4 pages/second. If i stop the scroll wheel at the two page mark (after 1 second), it continues to scroll the remaining 2 pages. This is quite hard to explain, but i hope you can understand

---

