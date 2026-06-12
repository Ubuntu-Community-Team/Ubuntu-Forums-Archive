---
title: "Onboard sound help required"
date: 2008-02-08
forum: General Help
---

### Post by CanonKen on 2008-02-08
Haven't been able to find anything thats likely to help me here so I posted this thread.
I have onboard sound and it works fine for playing cd's dvd's and ubuntu start up sounds etc.
i cannot get any sound when playing things like youtube vids - anyone any ideas?

Can't make head nor tale of these can you:)

```
ken@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ken@ubuntu:~$ 
```

```
ken@ubuntu:~$  lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
        Subsystem: ASRock Incorporation Unknown device 0746
        Flags: bus master, medium devsel, latency 0
        Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=02, sec-latency=32
        Memory behind bridge: cdd00000-cfefffff
        Prefetchable memory behind bridge: bda00000-cdbfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 0c00 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: ASRock Incorporation Unknown device 5513
        Flags: bus master, medium devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ff00 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASRock Incorporation Unknown device 7012
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at dc00 [size=256]
        I/O ports at d800 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: ASRock Incorporation Unknown device 8201
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at d400 [size=256]
        Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 70000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at d000 [size=256]
        Memory at cfffbf00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 21
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at cfee0000 [disabled] [size=128K]
        Capabilities: <access denied>

ken@ubuntu:~$ 
```

Any help appreciated

---

### Post by dcstar on 2008-02-09
> **CanonKen said:**
> Haven't been able to find anything thats likely to help me here so I posted this thread.
I have onboard sound and it works fine for playing cd's dvd's and ubuntu start up sounds etc.
i cannot get any sound when playing things like youtube vids - anyone any ideas?
..........
Any help appreciated

If the sound works then you have to find out why the application you are using to play these things doesn't use the working system - check its settings.

---

### Post by CanonKen on 2008-02-09
Thanks for your reply.
I use Firefox but I've been through the preferences in there and can't find anything, is there a plug-in or something I might be short of??

---

### Post by CanonKen on 2008-02-18
Still can't get sound with you tube videos, "some" flash files work, others don't.
Any ideas??

---

### Post by rosegarden78 on 2008-02-18
Gosh I don't know what to say ... maybe slow connection speed or need to max out your RAM?
[http://ubuntuforums.org/showthread.php?t=679165&highlight=abc.com](http://ubuntuforums.org/showthread.php?t=679165&highlight=abc.com)

edit: I meant for XP VirtualBox old laptop need max RAM or 1024 MB+ for two operating systems and smoother video. Check [www.speedtest.net](www.speedtest.net) and System Monitor for network speed.

---

### Post by strabes on 2008-02-18
Does sound work in firefox for playing other files like audio?

---

### Post by CanonKen on 2008-02-18
Thanks for your suggestions, yeah other sound files work Ok, connection speed OK, not sure what you mean when you say max out the ram but I have 1.5gb
Anyway - just been and borrowed a sound card, slotted that in and everything works OK, must be something to do with my on-board sound, had to take the card back straight away so will be out shopping at the weekend :)

---

