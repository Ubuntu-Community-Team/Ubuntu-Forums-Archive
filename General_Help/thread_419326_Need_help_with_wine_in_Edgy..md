---
title: "Need help with wine in Edgy."
date: 2007-04-22
forum: General Help
---

### Post by leroy_30 on 2007-04-22
I have finally taken the plunge and totally removed Winblows from my machine and gone totally Ubuntu. :) 

I have 1 actually 2 problems.

The first (no support for the ATI Theater 550 chipset) apparently can't be fixed. :mad: However I'll get over it.

The second is, I'm trying to run an application under wine and when It starts up I get the following error.

> "Application" only works with 16 or 32 bit desktops. Change your display settings appropriately.

"Application" will now exit.

I realize this error is specific to the app, but I'm wondering if wine is reporting like an 8 bit desktop or something. I don't know much about wine and could really use some help.

Also when I run winecfg I get:

> libGL warning: 3D driver claims to not support visual 0x5b

before winecfg starts. Could this be part of the problem?

Thanx in advance.

---

### Post by Martje_001 on 2007-04-23
"libGL warning: 3D driver claims to not support visual 0x5b" means your videocart has no (full) 3D-support. I have it too, but I can run windows programs fine with wine, so I don't think that's the problem

---

### Post by rich.bradshaw on 2007-04-23
Which version of Ubuntu are you using? 32 or 64 bit?

---

### Post by ashz on 2007-04-23
i would guess its talking about colour depth more than anything else suggest you goto WineHQ and ask them [http://www.winehq.com/](http://www.winehq.com/)...

more details on ur hardware would help though!!

cheers
ash

---

### Post by leroy_30 on 2007-04-23
I am using 32 bit version.

lspci -v gives

> 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 01c4
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
        Region 1: I/O ports at ecd8 [size=8]
        Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Region 3: Memory at dff40000 (32-bit, non-prefetchable) [size=256K]

---

### Post by leroy_30 on 2007-04-23
This morning I ran into this error

> libGL warning: 3D driver claims to not support visual 0x5b 

again while trying to start beryl. Beryl wouldn't start but when I ran

```
**sudo beryl-manager**
```

it still gives the error but beryl still works great.

---

