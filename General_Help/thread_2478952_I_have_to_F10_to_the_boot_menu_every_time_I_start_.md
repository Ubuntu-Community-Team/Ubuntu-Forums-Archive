---
title: "I have to F10 to the boot menu every time I start up"
date: 2022-09-09
forum: General Help
---

### Post by stevermann on 2022-09-09
I bought a used Intel NUC i3 off eBay. It seemed like a good deal. I installed a new MSATA drive and installed Ubuntu Desktop.  Everything went as usual.
But every time I boot or reboot, I have to hit F10 to get to the boot menu. In the boot menu the SATA drive is the only device, I just hit return and Ubuntu boots normally.

I went into the BIOS and determined that the SATA drive was the first boot device.

When I reboot, I get:
"A bootable device has not been detected"

Any idea why the SATA device is not detected as bootable, even though it boots fine when I go through the boot menu?

---

### Post by tea for one on 2022-09-09
Some suggestions:-

Install in UEFI mode
Insert your USB installer and see which device boots (without F10)
Reset the UEFI firmware to default and disable Secure Boot.
Update the Visual Bios for your NUC?

---

### Post by stevermann on 2022-09-09
Thanks. UEFI fixed it.

---

### Post by tea for one on 2022-09-09
> **stevermann said:**
> Thanks. UEFI fixed it.

UEFI install or UEFI update or reset UEFI to default?

---

