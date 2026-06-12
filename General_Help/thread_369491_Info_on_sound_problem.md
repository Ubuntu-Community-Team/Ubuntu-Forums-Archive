---
title: "Info on sound problem"
date: 2007-02-24
forum: General Help
---

### Post by keithk50 on 2007-02-24
Hi,   Since installation of Ubuntu on my laptap 3 days ago I have had no sound at all.   I still get sound when I boot into Windows XP.   I found a good guide by 'LordRaiden' (Comprehensive Guide) which I followed but no joy.    Here is the info from my Terminal:

aplay -l:

********List of PLAYBACK Hardware Devices*********
card 0:   SI7012  [SiS SI7012],   device 0:  Intel   ICH  [SiS  SI7012]
   Subdevices:  1/1
   Subdevice  #0:  subdevice  #0

I take it that this means that my soundcard is recognised?   When I type 'lspci' into Terminal it comes up with a lot of info and mentions the soundcard (SiS) however I do not know how to copy & paste the info from Terminal into my post!   Any help there?
I think I require a Linux Driver but I do not have a clue where to get it and how to install it.   Sorry.   Being a first timer I am finding it difficult working in Terminal (but enjoying the experience).   Have managed to get my Network Card to work, set up email, ugraded Firefox from 1.5 to 2.0 etc.   The lack of sound is really bugging me now.   All sliders in the alsamixer are un-muted and upto about 80% volume.

Any help and guidance would be greatly appreciated but please remember that I am brand new to Ubuntu.
Thanks.     Keith   (Ubuntu 6.0.6.1)

---

### Post by paydaydaddy on 2007-02-24
Word of Caution: I am a noob. That said I have some experience with a similar problem. You need to see if you can find more info on the sound card or integrated sound you have on your laptop. A google search should give you the info if you don't have the manual. Once you are armed with the correct info go back to the comprehensive guide and follow the link to the alsa project site. You should be able to find and download the correct drivers from there. If you get that far and then get stuck, ask for help on the forum for further instructions.

---

### Post by keithk50 on 2007-02-25
Thanks Paydaydaddy.   Any support is appreciated and I shall soldier on.        Keith.

---

### Post by drpaul on 2007-02-25
I have the Intel sound chips on my laptop and found that I got much better sound performance by installing a more recent version of the Alsa driver. Search the Hardware/Laptop forum for instructions.

HTH

Paul

---

### Post by geruss on 2007-02-25
Hi!
I have the same problem with my laptop. here is some output:

 aplay -l
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: SI7012 [SiS SI7012], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: Intel ICH [SiS SI7012]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0

lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: df600000-df6fffff
        Prefetchable memory behind bridge: cd500000-dd4fffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
        Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 128
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1816
        Flags: medium devsel, IRQ 177
        I/O ports at e400 [size=256]
        I/O ports at e000 [size=128]
        Capabilities: <access denied>

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1193
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 185
        Memory at dfffc000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 193
        Memory at dfffd000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 201
        Memory at dfffe000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 209
        Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1455
        Flags: bus master, medium devsel, latency 64, IRQ 217
        I/O ports at d800 [size=256]
        Memory at dfffb000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at dffc0000 [disabled] [size=128K]
        Capabilities: <access denied>

00:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 168, IRQ 169
        Memory at 24000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 217
        Memory at dfffa000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:09.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at dfffa800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: medium devsel, IRQ 10
        Memory at dfffac00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1921
        Flags: 66MHz, medium devsel, IRQ 11
        BIST result: 00
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at df6e0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at bc00 [size=128]
        Capabilities: <access denied>

---

