---
title: "hardy (or gutsy) fakeraid"
date: 2008-04-27
forum: General Help
---

### Post by b0b138 on 2008-04-27
When duel booting with xp, can the two use the same mirrored drives formatted as ntfs? Or will linux want to break and reset the mirror, which is what I absolutely DO NOT want to happen. My storage drive is mirrored for a reason, hard backup.

---

### Post by mcvf on 2009-01-26
Hello,
yes, Ubuntu can see the fakeraid mirror the same way Windows does without breakign anything. Though, installation is little more tricky - you have to install dmraid package and initialize it. Then you can continue with standard install procedure, just, before you reboot - make sure dmraid package is also installed in your Linux on the harddrive, not only in installation ramdisk ...
Also, you have to trick GRUB slightly to do job on fakeraid.

Cheers,

MCVF

---

### Post by mcvf on 2009-01-26
Quite detailed manual how to do that:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

