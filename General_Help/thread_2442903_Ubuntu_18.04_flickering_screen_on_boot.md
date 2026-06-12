---
title: "Ubuntu 18.04 flickering screen on boot"
date: 2020-05-09
forum: General Help
---

### Post by joshop on 2020-05-09
My computer had graphics problems so I tried updating graphics drivers and that led me here. Now, whenever I try to boot it stops at a log screen, the kind you'd see in recovery mode, then repeatedly flickers to a black screen for a few seconds, then back. I believe that it is attempting to start the Xorg server and failing. I have reason to believe (due to past errors) that it's some kind of "Segmentation fault at address 0x50" but I don't know much else. I am unable to log in using Alt+F2 because it continues flickering. I'm using an AMD Ryzen 5 3500U with integrated Radeon graphics. To make matters worse my xorg.conf.d was deleted and I don't know how to get Xorg to repopulate it.

---

### Post by joshop on 2020-05-09
I looked at the Xorg.0.log in recovery mode and some notable lines are there:
```
(EE) open /dev/dri/card0: No such file or directory
```
```
(EE) Screen 0 deleted because of no matching config section.
```
```
(EE) AIGLX: reverting to software rendering
```

---

