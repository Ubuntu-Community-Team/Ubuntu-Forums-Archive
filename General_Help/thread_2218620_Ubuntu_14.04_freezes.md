---
title: "Ubuntu 14.04 freezes"
date: 2014-04-21
forum: General Help
---

### Post by saleh2 on 2014-04-21
I recently migrated to Ubuntu 14.04 from mint. But My ubuntu freezes alot! It Badly freezes and hangs. I just can restart my PC.
in log file there's this error:

```
acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.307070] PCI host bridge to bus 0000:00
[    0.307073] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.307075] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.307077] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.307079] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.307081] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfeafffff]
[    0.307089] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.307107] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.307185] pci 0000:00:01.0: [8086:0045] type 01 class 0x060400
[    0.307219] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.307269] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.307337] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.307708] pci 0000:00:1a.0: reg 0x10: [mem 0xd9105c00-0xd9105fff]
[    0.309820] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.309894] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.309933] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.309955] pci 0000:00:1b.0: reg 0x10: [mem 0xd9100000-0xd9103fff 64bit]
[    0.310052] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.310113] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.310146] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.310245] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.310306] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.310338] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.310438] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.310498] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.310532] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.310632] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.310693] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.310732] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.311090] pci 0000:00:1d.0: reg 0x10: [mem 0xd9105800-0xd9105bff]
[    0.313195] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.313269] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.313311] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.313431] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.313462] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.313650] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601
[    0.313676] pci 0000:00:1f.2: reg 0x10: [io  0x5048-0x504f]
[    0.313687] pci 0000:00:1f.2: reg 0x14: [io  0x5054-0x5057]
[    0.313698] pci 0000:00:1f.2: reg 0x18: [io  0x5040-0x5047]
[    0.313709] pci 0000:00:1f.2: reg 0x1c: [io  0x5050-0x5053]
[    0.313720] pci 0000:00:1f.2: reg 0x20: [io  0x5020-0x503f]
[    0.313732] pci 0000:00:1f.2: reg 0x24: [mem 0xd9105000-0xd91057ff]
[    0.313799] pci 0000:00:1f.2: PME# supported from D3hot
[    0.313881] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.313902] pci 0000:00:1f.3: reg 0x10: [mem 0xd9106000-0xd91060ff 64bit]
[    0.313931] pci 0000:00:1f.3: reg 0x20: [io  0x5000-0x501f]
[    0.314084] pci 0000:01:00.0: [10de:0caf] type 00 class 0x030000
[    0.314098] pci 0000:01:00.0: reg 0x10: [mem 0xd2000000-0xd2ffffff]
[    0.314111] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.314125] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.314134] pci 0000:01:00.0: reg 0x24: [io  0x4000-0x407f]
[    0.314144] pci 0000:01:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[    0.314240] pci 0000:01:00.1: [10de:0be4] type 00 class 0x040300
[    0.314253] pci 0000:01:00.1: reg 0x10: [mem 0xd3000000-0xd3003fff]
[    0.314395] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.314398] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    0.314400] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.314403] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.314496] pci 0000:02:00.0: [10ec:8172] type 00 class 0x028000
[    0.314514] pci 0000:02:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.314526] pci 0000:02:00.0: reg 0x14: [mem 0xd8100000-0xd8103fff]
[    0.314637] pci 0000:02:00.0: supports D1 D2
[    0.314639] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.315306] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.321836] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.321847] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.321857] pci 0000:00:1c.0:   bridge window [mem 0xd8100000-0xd90fffff]
[    0.321870] pci 0000:00:1c.0:   bridge window [mem 0xd3100000-0xd40fffff 64bit pref]
[    0.322046] pci 0000:03:00.0: [1969:1063] type 00 class 0x020000
[    0.322137] pci 0000:03:00.0: reg 0x10: [mem 0xd7100000-0xd713ffff 64bit]
[    0.322183] pci 0000:03:00.0: reg 0x18: [io  0x2000-0x207f]
[    0.322584] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.323306] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.323430] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.323435] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.323440] pci 0000:00:1c.1:   bridge window [mem 0xd7100000-0xd80fffff]
[    0.323447] pci 0000:00:1c.1:   bridge window [mem 0xd4100000-0xd50fffff 64bit pref]
[    0.323524] pci 0000:00:1c.4: PCI bridge to [bus 09-0b]
[    0.323530] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    0.323534] pci 0000:00:1c.4:   bridge window [mem 0xd6100000-0xd70fffff]
[    0.323542] pci 0000:00:1c.4:   bridge window [mem 0xd5100000-0xd60fffff 64bit pref]
[    0.323621] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.323634] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.323636] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.323638] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.323640] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
[    0.324316] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.324371] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.324424] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.324477] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.324529] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.324582] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.324634] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.324686] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.324791] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.324795] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.324799] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.324860] PCI host bridge to bus 0000:ff
[    0.324863] pci_bus 0000:ff: root bus resource [bus ff]
[    0.324868] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    0.324908] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    0.324948] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    0.324983] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    0.325019] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    0.325053] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    0.325458] ACPI: Enabled 7 GPEs in block 00 to 3F
[    0.325467] ACPI: \_SB_.PCI0: notify handler is installed
[    0.325511] ACPI: \_SB_.CPBG: notify handler is installed
[    0.325522] Found 2 acpi root devices
[    0.325565] ACPI : EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.325673] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.325676] vgaarb: loaded
[    0.325677] vgaarb: bridge control possible 0000:01:00.0
[    0.325843] SCSI subsystem initialized
[    0.325908] libata version 3.00 loaded.
[    0.325930] ACPI: bus type USB registered
[    0.325947] usbcore: registered new interface driver usbfs
[    0.325954] usbcore: registered new interface driver hub
[    0.325978] usbcore: registered new device driver usb
[    0.326085] PCI: Using ACPI for IRQ routing
[    0.335918] PCI: pci_cache_line_size set to 64 bytes
[    0.335980] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    0.335982] e820: reserve RAM buffer [mem 0xbf63f000-0xbfffffff]
[    0.335983] e820: reserve RAM buffer [mem 0xbf800000-0xbfffffff]
[    0.336077] NetLabel: Initializing
[    0.336079] NetLabel:  domain hash size = 128
[    0.336080] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.336093] NetLabel:  unlabeled traffic allowed by default
[    0.336171] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.336176] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.338218] Switched to clocksource hpet
[    0.343117] AppArmor: AppArmor Filesystem Enabled
[    0.343153] pnp: PnP ACPI init
[    0.343168] ACPI: bus type PNP registered
[    0.343648] pnp 00:00: [dma 4]
```

---

### Post by coffeecat on 2014-04-21
Support not chat thread.

*Thread moved to **General Help**.*

---

### Post by Jonathan_Traill on 2014-04-21
When does it freeze?  Before the operating system loads (like mine) or after you reach the desktop?  Does it unfreeze if you leave it long enough?  Does the freeze when you try to do specific things, or randomly?  Or after you;ve been doing nothing for a while?

I have **no** solutions, but I'm trying to work out if you;re suffering the same slow boot issue I'm experiencing.

---

### Post by chenzero on 2014-10-16
I encountered the similiar error log in the dmesg.
from other post,
[http://askubuntu.com/questions/86499/error-about-acpi-osc-request-failed-ae-not-found](http://askubuntu.com/questions/86499/error-about-acpi-osc-request-failed-ae-not-found)
this log is  a warning, not a fatal error.

just as Jonathan said, I guess the "freeze" you mentioned is: it take a long time(in my computer, ~10min) to enter into desktop,
this is perhaps caused by settings in /etc/fstab

please ensure the passno (6th column) of / is set to 1, others should be 2 or 0, should NOT 1

HTH

---

