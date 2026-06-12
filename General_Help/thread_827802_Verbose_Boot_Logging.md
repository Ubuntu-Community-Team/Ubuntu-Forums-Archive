---
title: "Verbose Boot Logging?"
date: 2008-06-13
forum: General Help
---

### Post by kneewax on 2008-06-13
Hi Guys,  I am running Hardy on my Fujitsu-Siemens Amilo Pro v8010.  Since upgrading to hardy I have suffered exceptionally long boot times of 3 - 4 minutes - during boot the slider thingy under the Ubuntu logo stalls for considerable lengths of time.  I have tried booting in verbose mode, but the screen keeps scrolling before I have had chance to take note of where the bot process sticks.  Right at the beginning of boot there is an error about being 'unable to allocate PCI...." but it flies by so quickly I cannot read it all.

Is there a sensible way to get the verbose boot screens to log to a text file - so I can see exactly what is going on?

Ta
Kneewax

---

### Post by forestpixie on 2008-06-13
Have you checked your system logs (Sys >Admin>System Logs) yet for any errors.

---

### Post by kneewax on 2008-06-13
Yes, but to be honest there is so much stuff in there I am not sure what I am looking for?

---

### Post by VMC on 2008-06-13
You can also look at dmesg from a Terminal. See if anything reflects your problem.

Here's another thing that will definitely show where your boot time goes. It's called bootchart. Install from Terminal
```
sudo apt-get install bootchart
```
Then come back with the picture it creates at "/var/log/bootchart".
It showed me that my boot time was 31 seconds.

---

### Post by webaake on 2008-06-13
You could also edit menu.lst and remove;
 quiet splash

after the current kernel entry.

That'll show the boot process and you should be able to see where the snag is.

---

### Post by forestpixie on 2008-06-13
> **kneewax said:**
> Yes, but to be honest there is so much stuff in there I am not sure what I am looking for?

Why don't you post the output of

```
dmesg
```

Can you enclose it in code tags 
[code] at beginning and [[COLOR="White"].[/COLOR]/code] at the end

---

### Post by kneewax on 2008-06-14
OK here goes, but it is long!

[   13.725843] Early unpacking initramfs... done
[   14.048405] ACPI: Core revision 20070126
[   14.048475] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.074701] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
[   14.074723] Total of 1 processors activated (4026.58 BogoMIPS).
[   14.074909] ENABLING IO-APIC IRQs
[   14.075094] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.219562] Brought up 1 CPUs
[   14.219588] CPU0 attaching sched-domain:
[   14.219590]  domain 0: span 01
[   14.219591]   groups: 01
[   14.219738] net_namespace: 64 bytes
[   14.219746] Booting paravirtualized kernel on bare hardware
[   14.220143] Time:  5:53:35  Date: 06/14/08
[   14.220166] NET: Registered protocol family 16
[   14.220327] EISA bus registered
[   14.220352] ACPI: bus type pci registered
[   14.220820] PCI: PCI BIOS revision 2.10 entry at 0xfd954, last bus=6
[   14.220822] PCI: Using configuration type 1
[   14.220824] Setting up standard PCI resources
[   14.225348] ACPI: EC: Look up EC in DSDT
[   14.226736] ACPI: Interpreter enabled
[   14.226739] ACPI: (supports S0 S3 S4 S5)
[   14.226750] ACPI: Using IOAPIC for interrupt routing
[   14.226991] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   14.232724] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   14.232726] ACPI: EC: driver started in interrupt mode
[   14.232758] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.233482] Force enabled HPET at base address 0xfed00000
[   14.233488] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   14.233492] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   14.234345] PCI: Transparent bridge - 0000:00:1e.0
[   14.234419] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.234694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   14.240966] ACPI: PCI Interrupt Link [LNKA] (IRQs 11) *10
[   14.241043] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[   14.241118] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[   14.241193] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[   14.241267] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *10
[   14.241341] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[   14.241416] ACPI: PCI Interrupt Link [LNKG] (IRQs 11) *0, disabled.
[   14.241491] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[   14.241587] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.241612] pnp: PnP ACPI init
[   14.241619] ACPI: bus type pnp registered
[   14.244307] pnp: PnP ACPI: found 10 devices
[   14.244309] ACPI: ACPI bus type pnp unregistered
[   14.244314] PnPBIOS: Disabled by ACPI PNP
[   14.244496] PCI: Using ACPI for IRQ routing
[   14.244498] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.244502] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   14.244504] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   14.244506] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   14.244508] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   14.244510] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   14.244512] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   14.275503] NET: Registered protocol family 8
[   14.275505] NET: Registered protocol family 20
[   14.275642] hpet clockevent registered
[   14.275648] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.275651] hpet0: 3 64-bit timers, 14318180 Hz
[   14.276683] AppArmor: AppArmor Filesystem Enabled
[   14.279496] Time: tsc clocksource has been installed.
[   14.287523] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   14.287526] system 00:01: iomem range 0xf0000000-0xf0003fff could not be reserved
[   14.287529] system 00:01: iomem range 0xf0004000-0xf0004fff could not be reserved
[   14.287531] system 00:01: iomem range 0xf0005000-0xf0005fff could not be reserved
[   14.287534] system 00:01: iomem range 0xf0008000-0xf000bfff could not be reserved
[   14.287537] system 00:01: iomem range 0xfed20000-0xfed8ffff could not be reserved
[   14.287543] system 00:05: ioport range 0x680-0x6ff has been reserved
[   14.287545] system 00:05: ioport range 0x800-0x80f has been reserved
[   14.287548] system 00:05: ioport range 0x1000-0x107f has been reserved
[   14.287550] system 00:05: ioport range 0x1180-0x11bf has been reserved
[   14.287552] system 00:05: ioport range 0x1640-0x164f has been reserved
[   14.317890] PCI: Bridge: 0000:00:1c.0
[   14.317891]   IO window: disabled.
[   14.317896]   MEM window: disabled.
[   14.317900]   PREFETCH window: disabled.
[   14.317905] PCI: Bridge: 0000:00:1c.1
[   14.317907]   IO window: disabled.
[   14.317912]   MEM window: disabled.
[   14.317916]   PREFETCH window: disabled.
[   14.317927] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[   14.317929]   IO window: 00003400-000034ff
[   14.317934]   IO window: 00003800-000038ff
[   14.317939]   PREFETCH window: 54000000-57ffffff
[   14.317944]   MEM window: 58000000-5bffffff
[   14.317948] PCI: Bridge: 0000:00:1e.0
[   14.317951]   IO window: 3000-3fff
[   14.317956]   MEM window: b0100000-b01fffff
[   14.317960]   PREFETCH window: disabled.
[   14.317986] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   14.317993] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.318013] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   14.318020] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.318032] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.318049] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 16 (level, low) -> IRQ 17
[   14.318055] PCI: Setting latency timer of device 0000:06:09.0 to 64
[   14.318067] NET: Registered protocol family 2
[   14.355512] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.355707] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.356428] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.356859] TCP: Hash tables configured (established 131072 bind 65536)
[   14.356862] TCP reno registered
[   14.367596] checking if image is initramfs... it is
[   14.779247] Switched to high resolution mode on CPU 0
[   14.998690] Freeing initrd memory: 7722k freed
[   14.998901] Simple Boot Flag at 0x35 set to 0x1
[   14.999294] audit: initializing netlink socket (disabled)
[   14.999309] audit(1213422816.248:1): initialized
[   14.999472] highmem bounce pool size: 64 pages
[   15.001106] VFS: Disk quotas dquot_6.5.1
[   15.001175] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.001310] io scheduler noop registered
[   15.001312] io scheduler anticipatory registered
[   15.001314] io scheduler deadline registered
[   15.001324] io scheduler cfq registered (default)
[   15.001336] Boot video device is 0000:00:02.0
[   15.001622] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.001673] assign_interrupt_mode Found MSI capability
[   15.001718] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.001753] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.001854] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.001904] assign_interrupt_mode Found MSI capability
[   15.001943] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.001971] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.002192] isapnp: Scanning for PnP cards...
[   15.359012] isapnp: No Plug & Play device found
[   15.381790] Real Time Clock Driver v1.12ac
[   15.381900] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.382089] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[   15.382521] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[   15.382529] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   15.383430] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.383491] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.383576] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.385524] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.385528] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.394905] mice: PS/2 mouse device common for all mice
[   15.395001] EISA: Probing bus 0 at eisa.0
[   15.395008] Cannot allocate resource for EISA slot 1
[   15.395010] Cannot allocate resource for EISA slot 2
[   15.395012] Cannot allocate resource for EISA slot 3
[   15.395032] EISA: Detected 0 cards.
[   15.395035] cpuidle: using governor ladder
[   15.395037] cpuidle: using governor menu
[   15.395122] NET: Registered protocol family 1
[   15.395146] Using IPI No-Shortcut mode
[   15.395180] registered taskstats version 1
[   15.395288]   Magic number: 12:916:870
[   15.395333]   hash matches device ptyw8
[   15.395341]   hash matches device ptytb
[   15.395380] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.395382] EDD information not available.
[   15.395562] Freeing unused kernel memory: 368k freed
[   15.430843] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.588128] fuse init (API version 7.9)
[   16.606810] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.606825] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   16.608213] ACPI: Thermal Zone [THRM] (42 C)
[   17.094949] usbcore: registered new interface driver usbfs
[   17.094970] usbcore: registered new interface driver hub
[   17.097895] usbcore: registered new device driver usb
[   17.109867] USB Universal Host Controller Interface driver v3.0
[   17.109928] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   17.109939] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.109943] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.110268] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   17.110300] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   17.110421] usb usb1: configuration #1 chosen from 1 choice
[   17.110442] hub 1-0:1.0: USB hub found
[   17.110448] hub 1-0:1.0: 2 ports detected
[   17.216217] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   17.216230] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.216234] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.216254] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   17.216286] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   17.216386] usb usb2: configuration #1 chosen from 1 choice
[   17.216406] hub 2-0:1.0: USB hub found
[   17.216411] hub 2-0:1.0: 2 ports detected
[   17.298252] SCSI subsystem initialized
[   17.317823] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   17.317835] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.317840] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.317860] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   17.317891] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001860
[   17.317985] usb usb3: configuration #1 chosen from 1 choice
[   17.318010] hub 3-0:1.0: USB hub found
[   17.318015] hub 3-0:1.0: 2 ports detected
[   17.339185] libata version 3.00 loaded.
[   17.421774] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   17.421786] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   17.421790] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   17.421811] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   17.421843] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   17.421947] usb usb4: configuration #1 chosen from 1 choice
[   17.421968] hub 4-0:1.0: USB hub found
[   17.421973] hub 4-0:1.0: 2 ports detected
[   17.453656] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   17.525796] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   17.525810] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   17.525814] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   17.525835] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   17.529744] ehci_hcd 0000:00:1d.7: debug port 1
[   17.529750] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   17.529756] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xb0040000
[   17.577586] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.577688] usb usb5: configuration #1 chosen from 1 choice
[   17.577710] hub 5-0:1.0: USB hub found
[   17.577716] hub 5-0:1.0: 8 ports detected
[   17.681736] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.681766] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 20
[   17.681986] eth0: RTL8169sb/8110sb at 0xf8838000, 00:c0:9f:9c:a2:d8, XID 10000000 IRQ 20
[   17.682548] ACPI: PCI Interrupt 0000:06:09.2[C] -> GSI 18 (level, low) -> IRQ 21
[   17.732690] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[b0106800-b0106fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   17.735676] ahci 0000:00:1f.2: version 3.0
[   17.735695] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   17.735715] ahci 0000:00:1f.2: nr_ports (4) and implemented port map (0x5) don't match, using nr_ports
[   17.735718] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf
[   17.973347] usb 1-1: device not accepting address 2, error -71
[   18.273172] Clocksource tsc unstable (delta = -64996685376 ns)
[   18.277173] Time: hpet clocksource has been installed.
[   18.287400] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[   18.287404] ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
[   18.287409] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.287642] scsi0 : ahci
[   18.287812] scsi1 : ahci
[   18.287919] scsi2 : ahci
[   18.288025] scsi3 : ahci
[   18.288092] ata1: SATA max UDMA/133 abar m1024@0xb0040c00 port 0xb0040d00 irq 20
[   18.288096] ata2: SATA max UDMA/133 abar m1024@0xb0040c00 port 0xb0040d80 irq 20
[   18.288099] ata3: SATA max UDMA/133 abar m1024@0xb0040c00 port 0xb0040e00 irq 20
[   18.288102] ata4: SATA max UDMA/133 abar m1024@0xb0040c00 port 0xb0040e80 irq 20
[   18.294554] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f000054bff7]
[   18.297912] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   18.299768] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   18.299907] ata1.00: ATA-7: SAMSUNG HM080JI, YC100-02, max UDMA7
[   18.299910] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   18.300072] ata1.00: configured for UDMA/133
[   18.302885] usb 1-1: configuration #1 chosen from 1 choice
[   18.351389] ata2: SATA link down (SStatus 0 SControl 0)
[   18.352450] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   18.356307] usb 2-1: configuration #4 chosen from 1 choice
[   18.370923] ata3: SATA link down (SStatus 0 SControl 300)
[   18.374474] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   18.377982] ata4: SATA link down (SStatus 0 SControl 0)
[   18.378093] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM080JI  YC10 PQ: 0 ANSI: 5
[   18.382609] ata_piix 0000:00:1f.1: version 2.12
[   18.382626] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[   18.382658] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.384195] scsi4 : ata_piix
[   18.384340] scsi5 : ata_piix
[   18.384759] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   18.384762] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   18.385719] usb 4-1: configuration #1 chosen from 1 choice
[   18.386757] usbcore: registered new interface driver hiddev
[   18.391032] input: Elan USB Phone as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.3/input/input2
[   18.396542] input,hidraw0: USB HID v1.00 Device [Elan USB Phone] on usb-0000:00:1d.0-1
[   18.400492] input:  X M - 0 2 2 A            X M - 0 2 2 A           as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:4.0/input/input3
[   18.400750] input,hidraw1: USB HID v1.00 Keyboard [ X M - 0 2 2 A            X M - 0 2 2 A          ] on usb-0000:00:1d.1-1
[   18.401673] input: USB Mouse               as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input4
[   18.401948] input,hidraw2: USB HID v1.10 Mouse [USB Mouse              ] on usb-0000:00:1d.3-1
[   18.401958] usbcore: registered new interface driver usbhid
[   18.401961] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   18.438934] ata5.00: ATAPI: HL-DT-ST DVD-RW GCA-4080N, 0W33, max UDMA/33
[   18.442651] ata5.00: configured for UDMA/33
[   18.442692] ata6: port disabled. ignoring.
[   18.443101] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-RW GCA-4080N 0W33 PQ: 0 ANSI: 5
[   18.451708] Driver 'sd' needs updating - please use bus_type methods
[   18.451773] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   18.451784] sd 0:0:0:0: [sda] Write Protect is off
[   18.451786] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.451799] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.451839] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   18.451848] sd 0:0:0:0: [sda] Write Protect is off
[   18.451850] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.451862] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.451866]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   18.469004]  sda1 sda2 sda3 < sda5 >
[   18.469708] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.474622] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.474639] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   18.476384] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   18.476387] Uniform CD-ROM driver Revision: 3.20
[   18.476422] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   18.550283] Attempting manual resume
[   18.550286] swsusp: Resume From Partition 8:5
[   18.550288] PM: Checking swsusp image.
[   18.550351] PM: Resume from disk failed.
[   18.564435] kjournald starting.  Commit interval 5 seconds
[   18.564443] EXT3-fs: mounted filesystem with ordered data mode.
[   21.572818] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.644783] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.840621] iTCO_vendor_support: vendor-support=0
[   21.880594] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   21.880669] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   21.880699] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.940559] Linux agpgart interface v0.102
[   21.984042] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   22.049505] irda_init()
[   22.049522] NET: Registered protocol family 23
[   22.179863] input: Power Button (FF) as /devices/virtual/input/input6
[   22.204404] ACPI: Power Button (FF) [PWRF]
[   22.204458] input: Lid Switch as /devices/virtual/input/input7
[   22.216908] ACPI: Lid Switch [LID]
[   22.289267] ACPI: AC Adapter [ACAD] (on-line)
[   22.349789] ACPI: Battery Slot [BAT1] (battery present)
[   22.452251] intel_rng: FWH not detected
[   22.496262] agpgart: Detected an Intel 915GM Chipset.
[   22.496709] agpgart: Detected 7932K stolen memory.
[   22.514821] agpgart: AGP aperture is 256M @ 0xc0000000
[   22.672908] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   22.672938] nsc-ircc, chip->init
[   22.672950] nsc-ircc, Found chip at base=0x02e
[   22.672985] nsc-ircc, driver loaded (Dag Brattli)
[   22.672991] nsc_ircc_open(), can't get iobase of 0x2f8
[   22.673029] nsc-ircc, Found chip at base=0x02e
[   22.673063] nsc-ircc, driver loaded (Dag Brattli)
[   22.673066] nsc_ircc_open(), can't get iobase of 0x2f8
[   22.673082] nsc-ircc, chip->init
[   22.673094] nsc-ircc, Found chip at base=0x02e
[   22.673128] nsc-ircc, driver loaded (Dag Brattli)
[   22.673340] nsc-ircc 00:09: disabled
[   22.812026] ieee80211_crypt: registered algorithm 'NULL'
[   22.852987] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   22.852991] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   23.160060] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input8
[   23.191813] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   23.192301] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   23.223821] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   23.226080] Yenta: CardBus bridge found at 0000:06:09.0 [1734:107d]
[   23.226101] Yenta: Enabling burst memory read transactions
[   23.226106] Yenta: Using CSCINT to route CSC interrupts to PCI
[   23.226108] Yenta: Routing CardBus interrupts to PCI
[   23.226114] Yenta TI: socket 0000:06:09.0, mfunc 0x01ac1b22, devctl 0x64
[   23.347851] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   23.347855] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.456435] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   23.456440] Socket status: 30000006
[   23.456443] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   23.456446] cs: IO port probe 0x3000-0x3fff: clean.
[   23.456671] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   23.491677] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 17 (level, low) -> IRQ 16
[   23.513782] sdhci: Secure Digital Host Controller Interface driver
[   23.513786] sdhci: Copyright(c) Pierre Ossman
[   23.531849] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   24.016786] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[   24.049302] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   25.263117] usbcore: registered new interface driver snd-usb-audio
[   25.430387] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   25.430429] ACPI: PCI Interrupt 0000:06:09.3[A] -> GSI 16 (level, low) -> IRQ 17
[   25.430540] sdhci: SDHCI controller found at 0000:06:09.4 [104c:8034] (rev 0)
[   25.430557] ACPI: PCI Interrupt 0000:06:09.4[A] -> GSI 16 (level, low) -> IRQ 17
[   25.430569] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   25.430608] mmc0: SDHCI at 0xb0108400 irq 17 DMA
[   25.430618] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
[   25.430642] mmc1: SDHCI at 0xb0108000 irq 17 DMA
[   25.430651] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
[   25.430675] mmc2: SDHCI at 0xb0106400 irq 17 DMA
[   25.435565] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 16
[   25.435581] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   25.482295] cs: IO port probe 0x100-0x3af: clean.
[   25.483969] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.484681] cs: IO port probe 0x820-0x8ff: clean.
[   25.485278] cs: IO port probe 0xc00-0xcf7: clean.
[   25.486007] cs: IO port probe 0xa00-0xaff: clean.
[   25.504433] intel8x0_measure_ac97_clock: measured 54063 usecs
[   25.504435] intel8x0: clocking to 48000
[   25.607853] lp: driver loaded but no devices found
[   25.770467] Adding 489940k swap on /dev/sda5.  Priority:-1 extents:1 across:489940k
[   25.837307] EXT3 FS on sda1, internal journal
[   25.882430] device-mapper: uevent: version 1.0.3
[   25.882457] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   27.820736] /build/buildd/linux-2.6.24/drivers/usb/core/inode.c: usbfs: unrecognised mount option "devgid=121:ali" or missing value
[   27.820739] 
[   27.820743] /build/buildd/linux-2.6.24/drivers/usb/core/inode.c: usbfs: mount parameter error:
[   28.062445] ip_tables: (C) 2000-2006 Netfilter Core Team
[   28.263189] ACPI: ACPI Dock Station Driver 
[   28.779557] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[   28.779579] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[   28.786507] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 0 converters and GPIO not ready (0x1)
[   29.054474] ppdev: user-space parallel port driver
[   29.075818] audit(1213422920.915:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5471 profile="/usr/sbin/cupsd" namespace="default"
[   29.092789] apm: BIOS not found.
[   73.005870] Marking TSC unstable due to: cpufreq changes.
[   73.063894] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   73.063903] vboxdrv: Successfully done.
[   73.063970] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   73.063975] vboxdrv: Successfully loaded version 1.5.6 (interface 0x00050002).
[   29.649895] ttyS1: LSR safety check engaged!
[   29.752313] r8169: eth0: link up
[   74.602878] Bluetooth: Core ver 2.11
[   74.603636] NET: Registered protocol family 31
[   74.603642] Bluetooth: HCI device and connection manager initialized
[   74.603649] Bluetooth: HCI socket layer initialized
[   29.870332] Bluetooth: L2CAP ver 2.9
[   29.870337] Bluetooth: L2CAP socket layer initialized
[   29.899400] Bluetooth: RFCOMM socket layer initialized
[   29.899413] Bluetooth: RFCOMM TTY layer initialized
[   29.899414] Bluetooth: RFCOMM ver 1.8
[   75.110246] NET: Registered protocol family 17
[   31.168739] [drm] Initialized drm 1.1.0 20060810
[   39.030723] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   39.030733] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   39.030812] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   32.616943] NET: Registered protocol family 10
[   32.617139] lo: Disabled Privacy Extensions
[   89.235681] eth0: no IPv6 routers present
[   89.245165] eth1: no IPv6 routers present
[   41.600851] UDF-fs: No VRS found
[  114.044048] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  939.776382] UDF-fs: Partition marked readonly; forcing readonly mount
[  939.777765] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'JVC_DVD_ROM_PVD', timestamp 2003/12/31 19:56 (103c)
[  952.467282] UDF-fs: Partition marked readonly; forcing readonly mount
[  952.475027] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'JVC_DVD_ROM_PVD', timestamp 2003/12/31 19:56 (103c)

---

