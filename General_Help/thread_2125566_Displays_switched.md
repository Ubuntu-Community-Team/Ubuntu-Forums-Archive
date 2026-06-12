---
title: "Displays switched"
date: 2013-03-14
forum: General Help
---

### Post by BcRich on 2013-03-14
Hi,
After updating my 12.04 x64 installation, my display monitors switched around.
That is to say, I have two display monitors one is a 19 inch run off of an onboard GPU and the other is a 21 inch run off a PCI-X card. Both GPU's are AMD/ATI
Previously I had the 21 inch monitor as the main monitor and the 19 inch monitor as the secondary display, but after updating Ubuntu today the main monitor failed to work in anything other than safe graphics mode. So I reinstalled the ATI proprietary drivers by removing the old ones first then installing the latest 12.4 drivers. (There are 12.6 drivers available but these are beta).
So basically how do I change my 21 inch monitor back to being the main/default display?
Thanks

---

### Post by dino99 on 2013-03-14
i'm not used with catalyst, but you might have such settings into it i suppose. If you have an xorg.conf, delete it first.

---

### Post by QIII on 2013-03-14
What are the model numbers of each of the GPUs?

---

### Post by BcRich on 2013-03-14
Hi dino99
unfortunately no settings in catalyst to change the order of which display is primary, but lots of other useful settings :)
Hi QIII,
the onboard GPU is a HD4800 series and the PCIe is a HD6800 series

---

