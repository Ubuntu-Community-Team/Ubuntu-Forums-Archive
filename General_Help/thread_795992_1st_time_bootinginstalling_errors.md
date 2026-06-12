---
title: "1st time booting/installing errors"
date: 2008-05-16
forum: General Help
---

### Post by Yondergod22 on 2008-05-16
ok, the first time I booted I got this after the loading screen w/ the orange bar:
SQUASHFS error: sb_bread failed reading block 0x99ffe
SQUASHFS error: Unable to read page block 267f11a0, size e9cf

and its going up, and theres numbers on the left side going up.

then I restarted it and I got this:
busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) built in shell (ash)
enter 'help' for a list of built in commands
(initramfs)

and I found this that tells what to do for the busybox thing. 
[https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623](https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623)

but exaclty where do I put it in the boot line?
heres what it says after I press 'e'and stuff (I think this is the boot line?)
<UTF-8 console-setup/layoutcode=us console-setup/variantcode= --
where do I put irqpoll?

Thank you

---

### Post by ago on 2008-05-16
after --

---

### Post by ago on 2008-05-16
> **ago said:**
> after --

Please note that if it works for you with special parameters, it is often a good idea to also report a bug in launchpad, so that the issue can be properly addressed. The boot parameters are only workarounds for some special hardware.

---

### Post by Yondergod22 on 2008-05-17
ok, ill try that later.

---

