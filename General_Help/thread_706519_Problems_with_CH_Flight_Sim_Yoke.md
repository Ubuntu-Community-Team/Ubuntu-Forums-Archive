---
title: "Problems with CH Flight Sim Yoke"
date: 2008-02-24
forum: General Help
---

### Post by calums on 2008-02-24
I have a CH Flight Sim yoke which I'm using on a Fedora 8 installation with a KDE desktop. I have tried several times to get the yoke to work under several different versions of Ubuntu (latest one Gutsy) but when I go to the KDE control centre to calibrate the yoke and move any axis or press any button there is no movement displayed on the screen. This happens even though the yoke has been recognised as being on /dev/input/js0 correctly. If I lsusb, the yoke is displayed with: Bus 002 Device 002: ID 068e:00ff CH Products, Inc. Flight Sim Yoke. The only way to get the control center and any programme like X-Plane to be able to use it is to disconnect it, then reconnect, but this then puts the address to /dev/input/js1 so that all my settings in X-plane under /dev/input/js0 don't work. The yoke works perfectly under Fedora and even Sabayon but I can't see how to modify Ubuntu to get it working without unplugging it. I wondered if this is something to do with udev but I'm struggling to get my head round udev rules etc. I'd be grateful to hear from anyone with any suggestions how to overcome this problem.

---

