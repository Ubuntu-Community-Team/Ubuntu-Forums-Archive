---
title: "Changing Monitor Resolution"
date: 2008-03-30
forum: General Help
---

### Post by TheKid7 on 2008-03-30
I have tried many Linux Distros and have been running into a common problem with many of them, including Ubuntu. My Motherboard has VIA Unichrome Pro 2D On-Board Graphics. When Ubuntu is installed it typically sets the resolution at the maximum supported by the Monitor. I previously had a CRT (Max. 1600x1200). When the CRT burned out I got a LCD (Max 1280?x1024?). When I change the resolution to a lower value (say 1024x768) it usually works fine until I restart. On restart the screen is mostly black with some specks of light. I do not know how to recover from the mostly black screen so I usually either install a different distro or re-install the same distro.

The last time I installed Ubuntu I did not change the resolution and I restarted after install and Ubuntu said that it had a problem recognizing the video hardware so Ubuntu dropped the resolution to a low value.

1. How would you properly recover from this to avoid re-installing Ubuntu.
2. Any ideas on how to make it work at 1024x768. I have tried to switch from Vesa to Openchrome drivers but this usually fails the test.

Thank you.

P.S.: I am so frustrated with this problem that I have considered switching out this Motherboard with one that many people say works well with Ubuntu based distros.

---

### Post by housam on 2008-03-30
try this way.
type in a terminal
 ```
sudo dpkg-reconfigure xserver-xorg
```

and leave every thing as it is except the resolution you want to change.

---

