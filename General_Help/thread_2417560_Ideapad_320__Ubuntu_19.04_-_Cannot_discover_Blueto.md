---
title: "Ideapad 320 | Ubuntu 19.04 - Cannot discover Bluetooth mouse"
date: 2019-04-24
forum: General Help
---

### Post by GTMoraes on 2019-04-24
Hi,

I'm trying to pair and use a Logitech MX Anywhere 2 mouse, but Ubuntu 19.04 is unable to even find and list the Bluetooth mouse. It used to work on 18.04 before, and it does work on Windows and on an Android device.
Bluetooth is seemingly working fine, as it can detect my Android phone, two sets of wildly different speakers from my home, my TV, an unknown iPhone (presumably my neighbour) and even two devices from my car two stories down below...

I've tried pairing it directly on bluetoothctl, but even there it is unable to find this BT Mouse. I event tried getting the mouse MAC address from my Android phone and connecting blindly to it, but bluetoothctl just says "<MAC> not available."
I've restarted several times, slept and resumed, ran a couple of commands, disabled wi-fi during bluetooth scan.. all to no avail.

I'm out of ideas, what should I do now?

---

### Post by dino99 on 2019-04-24
If it was found and working with 18.04 on the same config, then :
- if it was a dist-upgrade, test with a 4.4 or 4.15 kernel  to narrow down the problem
- if its a fresh install on the same config, then check the metapackage is installed (ubuntu-desktop,...) and  glance at journalctl for errors.
- if that install is made on a different config, then be sure the bios/uefi usb activation is done, and check for errors logged too.

an old post, but can bring some light: [https://askubuntu.com/questions/636712/logitech-mx-anywhere-2-mouse-pairs-but-doesnt-do-anything](https://askubuntu.com/questions/636712/logitech-mx-anywhere-2-mouse-pairs-but-doesnt-do-anything)

---

### Post by GTMoraes on 2019-04-24
Hi,

I've Ubuntu 18.04 installed fresh on an external SSD and now 19.04 installed fresh on this laptop SSD. Booting 18.04, this version is able to discover, pair and use the bluetooth mouse, while on the 19.04 it is unable to even discover (i.e. "see" the bluetooth mouse in pairing mode). It's like the mouse isn't even there, while every other device is able to find that mouse.

I don't see any errors on journalctl. Maybe it won't say anything there anyway, because bluetooth is working fine otherwise.

I've a feeling that it is somehow using an incomplete or broken driver. The only time I couldn't pair this mouse somewhere was when using an old computer that didn't support Bluetooth 4.0 LE. 

------------------------

At the moment of writing this, the bluetooth mouse is now properly detected, has been paired and is now working.

I have absolutely no idea about what happened, but maybe some update went on without my knowledge. Other graphical corruption bug when recovering from sleep got fixed too, so I guess that was the case.

---

