---
title: "Any reccomendations?"
date: 2006-12-08
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-12-08
Here's the setup:

- ATI IXP northbridge video chip embedded video
- ECS rs482-m motherboard 
- Dapper

So my machine freezes like crazz, I get white lines and have to reset pc. It's practically unusable. I got beryl running though. Now I suspect my video is bad and causing the freezing, so i was thinking of getting a Nvidia graphics card. 

Any reccomendations? Anyone have a similiar setup? It's a 64-bit pc and I wanted to get it running well with beryl and no more freezing, plus using xrandr. :mrgreen:

---

### Post by strabes on 2006-12-08
Does X run fine without beryl? Does your card support the open source radeon driver? If you don't know you can check [here](https://help.ubuntu.com/community/BinaryDriverHowto). If it does support the open source driver then you should use AIGLX with beryl.

---

### Post by s_h_a_d_o_w_s on 2006-12-16
lspci gives me:

giga@ubuntuzilla:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

---

