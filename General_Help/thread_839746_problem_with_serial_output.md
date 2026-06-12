---
title: "problem with serial output"
date: 2008-06-24
forum: General Help
---

### Post by bekaar on 2008-06-24
hi all

im using 4-port serial (16550a) Universal PCI card its shows ttyS1 ,2 and 3 only with ttyS4 so how can i slove this im using ubunru 8.04

 20.948517] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.948608] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.948982] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.949081] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 18
[   20.949162] ttyS1: detected caps 00000700 should be 00000100
[   20.949168] 0000:05:00.0: ttyS1 at I/O 0xd000 (irq = 18) is a 16C950/954
[   20.949275] ttyS2: detected caps 00000700 should be 00000100
[   20.949281] 0000:05:00.0: ttyS2 at I/O 0xd008 (irq = 18) is a 16C950/954
[   20.949386] ttyS3: detected caps 00000700 should be 00000100
[   20.949392] 0000:05:00.0: ttyS3 at I/O 0xd010 (irq = 18) is a 16C950/954
[COLOR="Red"][   20.949422] Couldn't register serial port 0000:05:00.0: -28
[   20.949433] ACPI: PCI Interrupt 0000:05:00.1[B] -> GSI 19 (level, low) -> IRQ 17
[   20.949436] Couldn't register serial port 0000:05:00.1: -28
[/COLOR]

---

### Post by LinuxRocks713 on 2008-08-18
> **bekaar said:**
> hi all

im using 4-port serial (16550a) Universal PCI card its shows ttyS1 ,2 and 3 only with ttyS4 so how can i slove this im using ubunru 8.04

 20.948517] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.948608] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.948982] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.949081] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 18
[   20.949162] ttyS1: detected caps 00000700 should be 00000100
[   20.949168] 0000:05:00.0: ttyS1 at I/O 0xd000 (irq = 18) is a 16C950/954
[   20.949275] ttyS2: detected caps 00000700 should be 00000100
[   20.949281] 0000:05:00.0: ttyS2 at I/O 0xd008 (irq = 18) is a 16C950/954
[   20.949386] ttyS3: detected caps 00000700 should be 00000100
[   20.949392] 0000:05:00.0: ttyS3 at I/O 0xd010 (irq = 18) is a 16C950/954
[COLOR="Red"][   20.949422] Couldn't register serial port 0000:05:00.0: -28
[   20.949433] ACPI: PCI Interrupt 0000:05:00.1[B] -> GSI 19 (level, low) -> IRQ 17
[   20.949436] Couldn't register serial port 0000:05:00.1: -28
[/COLOR]

I think the error is because it already has four serial ports (ttyS0,ttyS1,ttyS2,ttyS3) and is trying to find/discover a fifth one.

---

