---
title: "Square mousepointer"
date: 2007-02-14
forum: General Help
---

### Post by adriaanvk on 2007-02-14
I have 2 screens, with both a separate xsession running:
xorg.conf:
Section "ServerLayout"
   Identifier     "Default Layout"
   Screen      0  "aticonfig-Screen[0]" 0 0
   Screen      1  "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]
   InputDevice    "Generic Keyboard"
   InputDevice    "Configured Mouse"
   InputDevice    "stylus" "SendCoreEvents"
   InputDevice    "cursor" "SendCoreEvents"
   InputDevice    "eraser" "SendCoreEvents"
   InputDevice    "Synaptics Touchpad"
EndSection

My first screen, laptop screen, is good, but the second screen displays a white square mousepointer of about 50pixels. In the past when this happens, it happens on both screens. After restarting xserver, all is fine.
But this day, i restarted again after bad mousepointer, but mousepointer still is a square on my second screen. How can i solve this problem?

---

