---
title: "help seeing hardware/busid"
date: 2008-01-17
forum: General Help
---

### Post by n0greenfx on 2008-01-17
ubuntu doesnt seem to see my onboard gpu it sees my nvidia card but not my onboard or mabey im looking wrong i was able to find it in mandravia i need to find out what the busid for it is? whats and easy command for that

---

### Post by fwojciec on 2008-01-17
> **n0greenfx said:**
> ubuntu doesnt seem to see my onboard gpu it sees my nvidia card but not my onboard or mabey im looking wrong i was able to find it in mandravia i need to find out what the busid for it is? whats and easy command for that

It should show up somewhere in the output of "lspci" -- the bus id will be the number to the left.

---

### Post by n0greenfx on 2008-01-17
i run that and it does not show up

---

### Post by n0greenfx on 2008-01-17
```
karl@karl-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
```
karl@karl-desktop:~$ 





i see the nvidia but where is the onboard gpu i kno its a via but i need the busid to write and xorg.config to run a dual monitor system

---

### Post by fwojciec on 2008-01-17
It's not there...  Maybe it deactivates itself when another card is connected...  Or maybe ubuntu doesn't see it for some reason...  Are you sure it's not disabled in bios or something?  No idea what to do about it, sorry.

---

