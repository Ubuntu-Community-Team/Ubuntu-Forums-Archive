---
title: "long delay when PCIe NIC installed"
date: 2017-03-23
forum: General Help
---

### Post by ideasman69 on 2017-03-23
Hi guys,

I'm having an issue with an older machine (specs below) that seems to pause for around 30-60 seconds on startup when I have a dual port PCIe NIC installed in the second x16 slot. When Ubuntu is freshly installed on the SSD without the NIC inserted, Ubuntu boots up within 10 seconds. As soon as the NIC is installed, I get the usual ubuntu grub coloured boot loader screen but then the screen goes into sleep mode for 30-60 seconds. After the delay, I get the ubuntu login screen and both NIC ports work fine. It almost seems like it's trying to poll the NIC as a video card or something?

So being newish to linux - i had a lot of trouble knowing what search terms to use. I'm sure others have seen this issue but not sure where to start. Happy to provide any info that can help find a workaround.

Specs:
Ubuntu Desktop 16.04.2
Supermicro C2SBX+ motherboard
Intel Core 2 Duo E7550
4GB DDR3
nVidia Quadro NVS300
Marvel Yukon Dual Port Server NIC

Any help or tips would be greatly appreciated. Thanks!

---

