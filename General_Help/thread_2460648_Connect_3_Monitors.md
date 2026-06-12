---
title: "Connect 3 Monitors"
date: 2021-04-15
forum: General Help
---

### Post by waffen on 2021-04-15
Hello,

I want to connect 3 monitors to my PC, actually I have 2 working fine.

Im using Ubuntu 20.04 uptodate, I have 2 video cards:
1. Integrated with the mainboard
2. Nvidia GeForce GT710 <- 2 monitors connected here, VGA and HDMI ports

So, is possible connect a third one to the integrated card (VGA port) and work with 3 monitors or I need something more?

Thanks!

---

### Post by CelticWarrior on 2021-04-15
Unless the motherboard explicitly support the multi-monitor / multi-head feature then it isn't possible because in order to use the dGPU the iGPU is automatically disabled.

---

### Post by waffen on 2021-04-15
Thanks for your answer! is there any way I can check it?

---

### Post by CelticWarrior on 2021-04-15
Yes, you can read the motherboard's manual and/or directly check at the firmware, UEFI or BIOS, settings.

---

### Post by HermanAB on 2021-04-15
You could also try a USB video adaptor.

---

### Post by waffen on 2021-04-17
Thanks for all the answers! I'll try with the USB adaptor, I'll need to buy one.

---

