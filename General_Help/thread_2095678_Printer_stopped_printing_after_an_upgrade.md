---
title: "Printer stopped printing after an upgrade"
date: 2012-12-17
forum: General Help
---

### Post by venik212 on 2012-12-17
Why is it that WITH EVERY "UPGRADE" of (L)ubuntu, my printer stops printing?  This has happened enough times to suspect that it is, somehow, built into the upgrade process-- break the old ways of printing.
Perusing the forums here I see that this is not my problem, but is reported repeatedly by many others.
It casts a serious shadow on the entire Ubuntu enterprise if such a vital function is lost twice a year due to upgrades.

Specifically, right now I cannot print from a Canon MF6530 usb-connected printer on (L)ubuntu 64 bit, 12.10.

---

### Post by tgalati4 on 2012-12-17
Yes, that is an issue with CUPS.  I'm not sure why but CUPS is intimately tied to the kernel.  When you upgrade the kernel it tends to break CUPS.  Have you tried to delete your printers completely and then re-add them?

Also, after an upgrade, there tend to be lots of patches that get pushed out.

In a terminal:

```
sudo apt-get update
sudo apt-get upgrade

```

---

