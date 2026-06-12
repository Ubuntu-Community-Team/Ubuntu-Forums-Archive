---
title: "Both PCI devices not detected"
date: 2007-11-01
forum: General Help
---

### Post by ~LoKe on 2007-11-01
About an hour ago I swapped everything out of my case and put it into a new one.  Now, upon boot, my PCI sound card and TV tuner are no longer detected.

> loke@x04d:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
Neither device is showing up.  What could be the problem?

---

### Post by bingoUV on 2007-11-01
Loose connections?

Any of the missing devices find mention in dmesg?

---

### Post by ~LoKe on 2007-11-01
I'll be sure to check the connections again, but first...anything here?

> loke@x04d:~$ dmesg|grep PCI
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:b0100000)
[   31.869644] PCI: PCI BIOS revision 3.00 entry at 0xfb420, last bus=5
[   31.869684] PCI: Using configuration type 1
[   31.869721] Setting up standard PCI resources
[   31.882220] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.882280] PCI: Probing PCI hardware (bus 00)
[   31.882881] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   31.882923] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   31.883708] PCI: Transparent bridge - 0000:00:1e.0
[   31.883805] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.883964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   31.884044] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   31.884125] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   31.884205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   31.899883] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   31.900366] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   31.900899] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   31.901379] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   31.901863] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   31.902395] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   31.902874] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   31.903353] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   31.906760] PCI: Using ACPI for IRQ routing
[   31.906798] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.970265] PCI: Bridge: 0000:00:01.0
[   31.970422] PCI: Bridge: 0000:00:1c.0
[   31.970578] PCI: Bridge: 0000:00:1c.3
[   31.970735] PCI: Bridge: 0000:00:1c.4
[   31.970893] PCI: Bridge: 0000:00:1e.0
[   31.971057] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.971134] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.971150] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.971226] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.971243] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[   31.971319] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   31.971334] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   31.972089] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.972099] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   32.687796] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   32.687944] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   32.688132] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   32.688317] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   33.977206] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.977287] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   34.079499] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[   34.079585] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   34.183586] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   34.183670] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   34.287243] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   34.287324] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   34.391124] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   34.391202] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   34.495033] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
[   34.495115] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   34.495250] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   34.602911] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   34.602991] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   34.603123] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   34.711288] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   34.711332] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
[   34.711434] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   35.034365] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   35.035012] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   35.588874] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
[   35.589650] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   35.920249] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   36.920608] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   47.721964] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.723909] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.118956] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.119044] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   48.857314] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.857402] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   49.046180] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   49.046276] PCI: Setting latency timer of device 0000:00:1b.0 to 64

---

