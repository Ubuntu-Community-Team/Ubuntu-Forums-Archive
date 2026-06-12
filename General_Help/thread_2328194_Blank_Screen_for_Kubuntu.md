---
title: "Blank Screen for Kubuntu"
date: 2016-06-18
forum: General Help
---

### Post by Tteddo on 2016-06-18
Is there a way in to just have the screen(s) blank after 60 minutes in Kubuntu 16.04? Not go to sleep, just blank. One of my monitors won't wake up without a power cycle.
All my searches find problems with black or blank screens on boot or other things. I tried installing gnome-screensaver to use that one but it froze X every couple of days. I added
```
Section "ServerFlags"
Option "BlankTime" "60"
EndSection
```
in xorg.conf but it's being ignored.

---

### Post by Tteddo on 2016-06-21
Was this feature removed for some reason? Anyone?

---

