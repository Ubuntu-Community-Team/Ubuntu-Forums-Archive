---
title: "xubuntu on SFF PC"
date: 2007-11-18
forum: General Help
---

### Post by hobbes69 on 2007-11-18
I installed xubuntu 7.10 on an old dell laptop (since it has a bootable CD drive) and then transferred the HD to a TPC-1260 which is a SFF PC and touchscreen LCD all in one. Everything appears to "run" but I'm having a few issues.

1. The touchscreen doesn't work right. I've installed the evtouch driver but can't seem to get it to work right. The y-axis seems to be swapped which I can fix but the pointer just goes all over the place.
2. The graphical boot sequence doesn't seem to use my xorg.conf and the size doesn't look right. Where can I fix that?
3. The X log shows it trying a bunch of modes (resolution, refresh, color depth, etc) even though I have the modes that work set.
4. In the greeter, the "Username:", "Language", and "Session" buttons are not in the right place. Is this a DPI issue? X is guessing 100 dpi.

Some hardware specs:
SFF PC w/ Trasmeta 500MHz processor.
128MB DRAM
SiliconMotion video (doc says 4MB, X reports 2MB)
12.1" LCD, 800x600 w/ touchscreen

Thanks,
Richard

---

### Post by hobbes69 on 2007-11-20
It looks like even though the touchscreen is manufactured by Electrographics, that it was customized to present a standard PS/2 interface as it needs no drivers under the intended OS of Windows CE. However, X seems to interpret it as joystick like. I can find different parts of the screen where I can almost get the mouse pointer to stay still and if I move farther away from that point the pointer accelerates.

'cat /proc/bus/input/devices ' shows the handlers as mouse1 and event2. Both of which I can use 'od /dev/input/event2' (or mouse1) can get 'stuff' to scroll down the screen. I've tried telling X to use both the ImPS/2 and PS/2 protocols but X rejects it.

Any ideas?

Thanks,
Richard

---

### Post by Flying caveman on 2007-11-21
This is way beyond my skill level, but I found this [http://ubuntuforums.org/showthread.php?t=158666](http://ubuntuforums.org/showthread.php?t=158666) which might help you.

---

