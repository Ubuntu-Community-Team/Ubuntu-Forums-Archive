---
title: "Ubuntu 12.04 Not Booting To Desktop"
date: 2013-03-27
forum: General Help
---

### Post by AP0ll0UK on 2013-03-27
I've come to use my Ubuntu box tonight and it was sat at the recovery screen so its rebooted for an unknown reason and halted.

Selecting the normal kernel just boots to a black screen and the box is inaccessible over WiFi.

Booting into Recovery shows a load of text which I believe refers to the WiFi card, things like -


rt3562sta: module license 'unspecified' taints kernel.
Disabling lock debugging due to kernel taint
==> rt2860_probe
rt2860 0000:07:06.0: PCI INT A ->  GSI 23 (level, low) -> IRQ 23
0000:07:06.0: at 0xfd6e0000, VA 0xf84c0000, IRQ 23
--> RTMPAllocationAdapterBlock

....then a number of TxRing entries with the last line being.....

STA Driver version-2.4.1.1


The machine hasn't installed any updates as it normally prompts to do this. It has been working fine and nothing has changed. 

I'm not too sure how to go about troubleshooting this to be honest. Is it a hardware failure and I should try boot the box without the WiFi card? Or should I rebuild it on the latest version of Ubuntu? I could if necessary as all my important data is held on other drives, the o/s drive is purely for Ubuntu and Apps.

Can anyone provide any guidance please?

---

