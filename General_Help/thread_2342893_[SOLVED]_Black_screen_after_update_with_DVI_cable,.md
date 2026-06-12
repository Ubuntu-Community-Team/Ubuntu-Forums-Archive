---
title: "[SOLVED] Black screen after update with DVI cable, but VGA cable ok (!)"
date: 2016-11-11
forum: General Help
---

### Post by dankegel on 2016-11-11
Running 16.04 with updates on an HP Pavillion 500-321 (i5-4570 Haswell) minitower,
I started having a black screen upon boot after an update about a week ago.
The system's up and happy, but the screen is black after the kernel sets the graphics mode.

Workarounds:
- Turning on nomodeset works, but that breaks accelerated 3d
- Reinstalling nonupdated 16.04 works (but letting it update breaks it again)
Non-workarounds:
- Updating to 16.10 does not help

Solution:
After troubleshooting a bit ( [https://bugs.launchpad.net/bugs/1639640](https://bugs.launchpad.net/bugs/1639640) ),
I guessed the kernel's DRM layer that has to do with the DVI cable might
have a regression... so I switched to a VGA cable instead, and the problem went away.
(Freaky, right?)

Anyone know what the upstream bug might be?

---

### Post by mörgæs on 2016-11-12
Thanks for attempting to mark the thread solved but if you use Thread Tools there is a better chance that people will find it.

---

