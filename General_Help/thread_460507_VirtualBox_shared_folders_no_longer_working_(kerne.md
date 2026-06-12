---
title: "VirtualBox shared folders no longer working (kernel update to blame?)"
date: 2007-05-31
forum: General Help
---

### Post by pointone on 2007-05-31
I run Windows XP Media Center Edition in VirtualBox under Ubuntu 7.04 Feisty Fawn.

A couple days ago, I installed a kernel update from 2.6.20-15 to 2.6.20-16 which required me to regenerate the VirtualBox kernel module. Since then, the shared folder I use to work between my guest and host machine has been failing randomly. The drive will connect when I first start Windows, but then crap out after a few minutes of use. I need to restart Windows for reconnection to be possible.

This all started after the kernel update, and I was wondering if anyone else is experiencing similar problems. Did the update break my VirtualBox installation, or is this simply a coincidence?

Any help would be appreciated. Cheers!

---

### Post by smoker on 2007-05-31
hi, have a look at this thread for an answer:
[http://ubuntuforums.org/showthread.php?t=457953&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=457953&highlight=virtualbox)

hope it helps:D

---

### Post by pointone on 2007-05-31
Nothing else is wrong with VirtualBox. I had that same problem with the kernel module, but successfully recreated it. Everything else is working fine in VirtualBox except my shared folder.

---

