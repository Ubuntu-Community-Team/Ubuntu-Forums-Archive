---
title: "Screen hangs purple after GRUB"
date: 2018-02-13
forum: General Help
---

### Post by spadavecchio on 2018-02-13
I have a 16.04 machine that was working fine today, until it decided to turn my screen blank (but the lights on the computer remained on, and the keyboard still seemed to have power). I turned off the machine, and turned it back on, and which point it asked to connect a bootable drive. I tried rebooting the machine again, after making sure all the wires were all plugged in, and now it boots to GRUB, and allows me to boot Ubuntu, but after that, it just goes to a purple screen and hangs. Is there any way of telling whats causing this issue? 

thanks

---

### Post by spadavecchio on 2018-02-13
I was able to boot into recovery mode, and then ran a manual fsck. It found/fixed a number of blocked/bad nodes. Rebooting after fsck seems to have fixed the issue; is there any idea as to what caused this? A bad drive?

---

