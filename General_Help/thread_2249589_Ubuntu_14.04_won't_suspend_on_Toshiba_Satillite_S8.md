---
title: "Ubuntu 14.04 won't suspend on Toshiba Satillite S855D-S5253"
date: 2014-10-23
forum: General Help
---

### Post by Halfdanr on 2014-10-23
Hello.  I'm running Lubuntu 14.04 on a Toshiba Satillite S855D-S5253 wth a AMD Quad-Core A10-4600M APU and 6 gbs of RAM.  The problem is that Ubuntu won't suspend or hibernate.
If I select "standby" from the shutdown menu the screen turns dark but the computer does not turn off.  Moving the mouse brings up the log in screen and I can log in.
The command pm-suspend powers off the computer for a second but it immediately wakes up again.

My "/var/log/pm-suspend.log" file is here: [http://paste.ubuntu.com/8640812](http://paste.ubuntu.com/8640812).

Graphics card info:
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7660G] [1002:9900] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:fb28]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at f0200000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon


Kernel:
BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=b44745e9-4e61-4a08-8392-4467d657f88d ro quiet splash vt.handoff=7



Thanks in advance for the help!

---

