---
title: "mouse doesn't work through evdev in hardy"
date: 2008-06-21
forum: General Help
---

### Post by ptero on 2008-06-21
i made a minimum installation of hardy and then installed and set up xorg and fluxbox. however, my old xorg.conf didn't work - xorg-server wouldn't find the mouse... however, it worked perfectly on my old gentoo and gutsy installations...

```
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "evdev"
        Option      "Name" "Saitek Saitek Laser Office Mouse"
EndSection
```

were there any changes for evdev in the new xorg or in hardy? i'd like it to work, because the back/forward buttons don't work with ImPS/2 or ExplorerPS/2

---

