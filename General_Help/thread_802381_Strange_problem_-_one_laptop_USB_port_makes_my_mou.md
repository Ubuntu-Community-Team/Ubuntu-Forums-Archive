---
title: "Strange problem - one laptop USB port makes my mouse cursor drag with slow movement"
date: 2008-05-21
forum: General Help
---

### Post by AaronMT on 2008-05-21
This is a new problem I never had before. I had to rearrange which devices use which ports on my laptop and one USB port, dedicated for my wireless mouse, on my laptop only under Ubuntu is making my mouse cursor drag and the movement is incredibly slow. What the heck is up with this?

It's almost as if this USB port is receiveing low priority or something. How can I resolve this issue?

---

### Post by phidia on 2008-05-21
What does lsusb -v (typed in a terminal) show?
You can also check your system and usb ports with dmesg.
Is this a 1.1 usb port?

---

### Post by AaronMT on 2008-05-21
Output of **lsusb -v**
- I also tried with a wired USB mouse and the results were the same. This port acted normally in previous Ubuntu versions as well as Vista/XP.

```

Bus 006 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12

Bus 005 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 001 Device 005: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc521 MX620 Laser Cordless Mouse
  bcdDevice           57.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      67
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      79
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
```

Output of **lsusb**

```
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 001 Device 001: ID 0000:0000  

```

Output of **dmesg**

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077e70000 (usable)
[    0.000000]  BIOS-e820: 0000000077e70000 - 0000000077e80000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077e80000 - 0000000077f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077f00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1022MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8530
[    0.000000] Entering add_active_range(0, 0, 491120) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   491120
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   491120
[    0.000000] On node 0 totalpages: 491120
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2044 pages used for memmap
[    0.000000]   HighMem zone: 259700 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8500 checksum 0
[    0.000000] ACPI: RSDP 000F8500, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 77E79653, 003C (r1 DELL    M08      6040000  LTP        0)
[    0.000000] ACPI: FACP 77E7FC6E, 0074 (r1 ATI    Bowfin    6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 77E7968F, 65DF (r1    ATI    SB600  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 77E90FC0, 0040
[    0.000000] ACPI: TCPA 77E7FCE2, 0032 (r2 AMD              6040000 PTEC        0)
[    0.000000] ACPI: SSDT 77E7FD14, 00F4 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 77E7FE08, 0046 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 77E7FE4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: SLIC 77E7FE8A, 0176 (r1 DELL    M08      6040000  LTP        0)
[    0.000000] ACPI: DMI detected: Dell
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: AMD      Product ID: POOH         APIC at: 0xFEE00000
[    0.000000] I/O APIC #1 Version 33 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487284
[    0.000000] Kernel command line: root=UUID=bfe82a56-74a0-4140-9e02-0d2b1e2c0350 ro quiet splash noapic apci=off
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1795.581 MHz processor.
[   15.542686] Console: colour VGA+ 80x25
[   15.542689] console [tty0] enabled
[   15.542997] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.543366] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.624177] Memory: 1935300k/1964480k available (2157k kernel code, 27976k reserved, 998k data, 364k init, 1046976k highmem)
[   15.624186] virtual kernel memory layout:
[   15.624187]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   15.624188]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.624189]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.624191]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.624192]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   15.624193]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   15.624194]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   15.624197] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.624233] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.704217] Calibrating delay using timer specific routine.. 3594.47 BogoMIPS (lpj=7188953)
[   15.704244] Security Framework initialized
[   15.704249] SELinux:  Disabled at boot.
[   15.704264] AppArmor: AppArmor initialized
[   15.704268] Failure registering capabilities with primary security module.
[   15.704277] Mount-cache hash table entries: 512
[   15.704389] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019 00000000
[   15.704399] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.704401] CPU: L2 Cache: 512K (64 bytes/line)
[   15.704404] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 00000019 00000000
[   15.704414] Compat vDSO mapped to ffffe000.
[   15.704425] Checking 'hlt' instruction... OK.
[   15.720489] SMP alternatives: switching to UP code
[   15.721644] Freeing SMP alternatives: 11k freed
[   15.721756] Early unpacking initramfs... done
[   16.078178] ACPI: Core revision 20070126
[   16.078247] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.080215] ACPI: setting ELCR to 0200 (from 0e00)
[   17.114781] CPU0: AMD Mobile AMD Sempron(tm) Processor 3500+ stepping 02
[   17.114801] Total of 1 processors activated (3594.47 BogoMIPS).
[   17.219527] Brought up 1 CPUs
[   17.219542] CPU0 attaching sched-domain:
[   17.219544]  domain 0: span 01
[   17.219546]   groups: 01
[   17.219695] net_namespace: 64 bytes
[   17.219702] Booting paravirtualized kernel on bare hardware
[   17.220160] Time: 16:47:27  Date: 05/21/08
[   17.220181] NET: Registered protocol family 16
[   17.220341] EISA bus registered
[   17.220369] ACPI: bus type pci registered
[   17.235736] PCI: BIOS BUG #81[49435000] found
[   17.235773] PCI: Using configuration type 1
[   17.235775] Setting up standard PCI resources
[   17.237381] ACPI: EC: Look up EC in DSDT
[   17.239358] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   17.239606] ACPI: Interpreter enabled
[   17.239609] ACPI: (supports S0 S3 S4 S5)
[   17.239620] ACPI: Using PIC for interrupt routing
[   17.239899] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.249230] ACPI: EC: GPE = 0x14, I/O: command/status = 0x66, data = 0x62
[   17.249233] ACPI: EC: driver started in interrupt mode
[   17.249267] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.249463] pci 0000:00:12.0: set SATA to AHCI mode
[   17.250748] PCI: Transparent bridge - 0000:00:14.4
[   17.250777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.250958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   17.251092] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   17.251238] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   17.251372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   17.254404] ACPI: PCI Interrupt Link [LNKA] (IRQs *10 11)
[   17.254517] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[   17.254626] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[   17.254734] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[   17.254841] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *9
[   17.254950] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[   17.255058] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[   17.255165] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   17.255274] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   17.255380] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.255405] pnp: PnP ACPI init
[   17.255412] ACPI: bus type pnp registered
[   17.257886] pnp: PnP ACPI: found 10 devices
[   17.257889] ACPI: ACPI bus type pnp unregistered
[   17.257892] PnPBIOS: Disabled by ACPI PNP
[   17.258086] PCI: Using ACPI for IRQ routing
[   17.258089] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.258095] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   17.258098] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   17.263510] NET: Registered protocol family 8
[   17.263512] NET: Registered protocol family 20
[   17.263570] AppArmor: AppArmor Filesystem Enabled
[   17.267461] Time: tsc clocksource has been installed.
[   17.275488] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.275491] system 00:01: iomem range 0x0-0x0 could not be reserved
[   17.275494] system 00:01: iomem range 0x0-0x0 could not be reserved
[   17.275501] system 00:08: ioport range 0x1080-0x1080 has been reserved
[   17.275504] system 00:08: ioport range 0x220-0x22f has been reserved
[   17.275507] system 00:08: ioport range 0x40b-0x40b has been reserved
[   17.275510] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   17.275512] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   17.275515] system 00:08: ioport range 0x530-0x537 has been reserved
[   17.275517] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   17.275520] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   17.275523] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   17.275525] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   17.275528] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   17.275531] system 00:08: ioport range 0xcd0-0xcd3 has been reserved
[   17.275533] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   17.275536] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   17.275539] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   17.275541] system 00:08: ioport range 0x8000-0x805f has been reserved
[   17.275544] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   17.275547] system 00:08: ioport range 0x87f-0x87f has been reserved
[   17.275552] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   17.275556] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   17.275559] system 00:09: iomem range 0xc0004800-0xc0004bff has been reserved
[   17.275562] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[   17.275564] system 00:09: iomem range 0x0-0xfff could not be reserved
[   17.305896] PCI: Bridge: 0000:00:01.0
[   17.305898]   IO window: 9000-9fff
[   17.305901]   MEM window: c0100000-c01fffff
[   17.305904]   PREFETCH window: c8000000-cfffffff
[   17.305907] PCI: Bridge: 0000:00:05.0
[   17.305908]   IO window: disabled.
[   17.305910]   MEM window: disabled.
[   17.305913]   PREFETCH window: disabled.
[   17.305915] PCI: Bridge: 0000:00:06.0
[   17.305917]   IO window: disabled.
[   17.305919]   MEM window: c0200000-c02fffff
[   17.305921]   PREFETCH window: disabled.
[   17.305924] PCI: Bridge: 0000:00:14.4
[   17.305926]   IO window: disabled.
[   17.305931]   MEM window: c0300000-c03fffff
[   17.305935]   PREFETCH window: disabled.
[   17.305955] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   17.305962] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   17.305978] NET: Registered protocol family 2
[   17.343494] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.343773] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.344478] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.344805] TCP: Hash tables configured (established 131072 bind 65536)
[   17.344808] TCP reno registered
[   17.355544] checking if image is initramfs... it is
[   17.807197] Switched to high resolution mode on CPU 0
[   18.039263] Freeing initrd memory: 7697k freed
[   18.039767] audit: initializing netlink socket (disabled)
[   18.039779] audit(1211388446.284:1): initialized
[   18.039940] highmem bounce pool size: 64 pages
[   18.041508] VFS: Disk quotas dquot_6.5.1
[   18.041570] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.041686] io scheduler noop registered
[   18.041688] io scheduler anticipatory registered
[   18.041690] io scheduler deadline registered
[   18.041703] io scheduler cfq registered (default)
[   18.041709] PCI: MSI quirk detected. MSI deactivated.
[   18.041765] Boot video device is 0000:01:05.0
[   18.041869] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.041890] assign_interrupt_mode Found MSI capability
[   18.041893] Allocate Port Service[0000:00:05.0:pcie00]
[   18.041922] Allocate Port Service[0000:00:05.0:pcie02]
[   18.041974] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   18.041994] assign_interrupt_mode Found MSI capability
[   18.041996] Allocate Port Service[0000:00:06.0:pcie00]
[   18.042022] Allocate Port Service[0000:00:06.0:pcie02]
[   18.042206] isapnp: Scanning for PnP cards...
[   18.396252] isapnp: No Plug & Play device found
[   18.420538] Real Time Clock Driver v1.12ac
[   18.420627] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.421599] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.421660] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.421740] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   18.424615] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.424619] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.426998] mice: PS/2 mouse device common for all mice
[   18.427095] EISA: Probing bus 0 at eisa.0
[   18.427102] Cannot allocate resource for EISA slot 1
[   18.427129] Cannot allocate resource for EISA slot 8
[   18.427131] EISA: Detected 0 cards.
[   18.427134] cpuidle: using governor ladder
[   18.427136] cpuidle: using governor menu
[   18.427217] NET: Registered protocol family 1
[   18.427240] Using IPI No-Shortcut mode
[   18.427272] registered taskstats version 1
[   18.427383]   Magic number: 8:504:793
[   18.427496]   hash matches device ptyr1
[   18.427544] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.427546] EDD information not available.
[   18.427783] Freeing unused kernel memory: 364k freed
[   18.489379] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.770062] fuse init (API version 7.9)
[   19.969981] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.969988] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.970000] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.987303] ACPI: Thermal Zone [THRM] (48 C)
[   20.819546] SCSI subsystem initialized
[   20.857476] libata version 3.00 loaded.
[   20.873722] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   20.873727] PCI: setting IRQ 11 as level-triggered
[   20.873732] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   20.873742] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   20.927158] usbcore: registered new interface driver usbfs
[   20.927184] usbcore: registered new interface driver hub
[   20.937470] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[   20.937759] ahci 0000:00:12.0: version 3.0
[   20.937948] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   20.937951] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[   20.937967] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   20.937969] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   20.939874] usbcore: registered new device driver usb
[   20.950370] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.993449] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.993455] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.940890] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   21.940895] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pio 
[   21.941246] scsi0 : ahci
[   21.941501] scsi1 : ahci
[   21.941626] scsi2 : ahci
[   21.941750] scsi3 : ahci
[   21.941823] ata1: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004100 irq 11
[   21.941827] ata2: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004180 irq 11
[   21.941831] ata3: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004200 irq 11
[   21.941835] ata4: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004280 irq 11
[   22.416591] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.417336] ata1.00: ATA-7: ST98823AS, 8.04, max UDMA/133
[   22.417339] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   22.421034] ata1.00: configured for UDMA/133
[   22.732409] ata2: SATA link down (SStatus 0 SControl 300)
[   23.044238] ata3: SATA link down (SStatus 0 SControl 300)
[   23.356060] ata4: SATA link down (SStatus 0 SControl 300)
[   23.356161] scsi 0:0:0:0: Direct-Access     ATA      ST98823AS        8.04 PQ: 0 ANSI: 5
[   23.358313] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   23.358317] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   23.358331] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   23.358594] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   23.358610] ohci_hcd 0000:00:13.0: irq 11, io mem 0xc0005000
[   23.367164] Driver 'sd' needs updating - please use bus_type methods
[   23.367241] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.367253] sd 0:0:0:0: [sda] Write Protect is off
[   23.367255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.367271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.367311] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.367320] sd 0:0:0:0: [sda] Write Protect is off
[   23.367322] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.367336] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.367339]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[   23.412162] hub 1-0:1.0: USB hub found
[   23.412176] hub 1-0:1.0: 2 ports detected
[   23.448090]  sda1 sda2 < sda5 >
[   23.476436] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.482210] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.516046] ACPI: Unable to derive IRQ for device 0000:00:13.1
[   23.516050] ACPI: PCI Interrupt 0000:00:13.1[B]: no GSI - using IRQ 11
[   23.516065] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   23.516086] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   23.516102] ohci_hcd 0000:00:13.1: irq 11, io mem 0xc0006000
[   23.572044] usb usb2: configuration #1 chosen from 1 choice
[   23.572067] hub 2-0:1.0: USB hub found
[   23.572076] hub 2-0:1.0: 2 ports detected
[   23.675985] ACPI: Unable to derive IRQ for device 0000:00:13.2
[   23.675989] ACPI: PCI Interrupt 0000:00:13.2[C]: no GSI - using IRQ 11
[   23.676005] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   23.676027] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   23.676042] ohci_hcd 0000:00:13.2: irq 11, io mem 0xc0007000
[   23.731978] usb usb3: configuration #1 chosen from 1 choice
[   23.732001] hub 3-0:1.0: USB hub found
[   23.732011] hub 3-0:1.0: 2 ports detected
[   23.819160] Attempting manual resume
[   23.819164] swsusp: Resume From Partition 8:5
[   23.819166] PM: Checking swsusp image.
[   23.819409] PM: Resume from disk failed.
[   23.835887] ACPI: Unable to derive IRQ for device 0000:00:13.3
[   23.835891] ACPI: PCI Interrupt 0000:00:13.3[B]: no GSI - using IRQ 11
[   23.835906] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   23.835929] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   23.835945] ohci_hcd 0000:00:13.3: irq 11, io mem 0xc0008000
[   23.868852] kjournald starting.  Commit interval 5 seconds
[   23.868863] EXT3-fs: mounted filesystem with ordered data mode.
[   23.891876] usb usb4: configuration #1 chosen from 1 choice
[   23.891899] hub 4-0:1.0: USB hub found
[   23.891909] hub 4-0:1.0: 2 ports detected
[   23.995780] ACPI: Unable to derive IRQ for device 0000:00:13.4
[   23.995784] ACPI: PCI Interrupt 0000:00:13.4[C]: no GSI - using IRQ 11
[   23.995800] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   23.995828] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   23.995844] ohci_hcd 0000:00:13.4: irq 11, io mem 0xc0009000
[   24.051784] usb usb5: configuration #1 chosen from 1 choice
[   24.051805] hub 5-0:1.0: USB hub found
[   24.051814] hub 5-0:1.0: 2 ports detected
[   24.155797] ACPI: Unable to derive IRQ for device 0000:00:13.5
[   24.155801] ACPI: PCI Interrupt 0000:00:13.5[D]: no GSI - using IRQ 11
[   24.155812] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   24.155836] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   24.155875] ehci_hcd 0000:00:13.5: debug port 1
[   24.155887] ehci_hcd 0000:00:13.5: irq 11, io mem 0xc0004400
[   24.167598] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.167688] usb usb6: configuration #1 chosen from 1 choice
[   24.167711] hub 6-0:1.0: USB hub found
[   24.167717] hub 6-0:1.0: 10 ports detected
[   24.271746] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
[   24.271932] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   24.271935] PCI: setting IRQ 10 as level-triggered
[   24.271939] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   24.271949] SB600_PATA: not 100% native mode: will probe irqs later
[   24.271958]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[   24.271968] Probing IDE interface ide0...
[   25.679114] hda: TSSTcorp DVD+/-RW TS-L632D, ATAPI CD/DVD-ROM drive
[   25.679148] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   25.679445] hda: UDMA/33 mode selected
[   25.679916] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   25.704299] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[   25.704303] ACPI: PCI Interrupt 0000:08:00.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[   25.762739] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[   25.762758] b44.c:v2.0
[   25.783009] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:50:fa:0a
[   31.861915] spurious 8259A interrupt: IRQ7.
[   32.682846] Linux agpgart interface v0.102
[   32.806753] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.870772] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.258613] input: Power Button (FF) as /devices/virtual/input/input2
[   33.270449] ACPI: Power Button (FF) [PWRF]
[   33.270547] input: Power Button (CM) as /devices/virtual/input/input3
[   33.286431] ACPI: Power Button (CM) [PWRB]
[   33.286536] input: Sleep Button (CM) as /devices/virtual/input/input4
[   33.302427] ACPI: Sleep Button (CM) [SLPB]
[   33.302534] input: Lid Switch as /devices/virtual/input/input5
[   33.310472] ACPI: Lid Switch [LID]
[   33.312594] ACPI: AC Adapter [ACAD] (on-line)
[   33.674459] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   33.996854] [fglrx] Maximum main memory to use for locked dma buffers: 1776 MBytes.
[   33.996890] [fglrx] ASYNCIO init succeed!
[   33.997009] [fglrx] PAT is enabled successfully!
[   33.998626] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   34.198059] ACPI: Battery Slot [BAT1] (battery present)
[   34.198109] ACPI: WMI-Acer: Mapper loaded
[   34.965468] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input6
[   34.981485] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   35.277369] b43-phy0: Broadcom 4311 WLAN found
[   35.377556] phy0: Selected rate control algorithm 'simple'
[   35.992401] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   36.330139] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   36.394119] hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   36.394127] Uniform CD-ROM driver Revision: 3.20
[   36.456666] ricoh-mmc: Ricoh MMC Controller disabling driver
[   36.456671] ricoh-mmc: Copyright(c) Philip Langdale
[   36.456745] ricoh-mmc: Ricoh MMC controller found at 0000:08:01.1 [1180:0843] (rev 1)
[   36.456750] ricoh-mmc: Main firewire function not found. Cannot disable controller.
[   36.560227] sdhci: Secure Digital Host Controller Interface driver
[   36.560231] sdhci: Copyright(c) Pierre Ossman
[   36.560272] sdhci: SDHCI controller found at 0000:08:01.0 [1180:0822] (rev 19)
[   36.560466] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[   36.560468] ACPI: PCI Interrupt 0000:08:01.0[B] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[   36.560488] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   36.560535] mmc0: SDHCI at 0xc0302000 irq 10 DMA
[   37.234753] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   37.506732] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   37.542523] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   37.574644] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   39.042762] lp: driver loaded but no devices found
[   39.321501] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   39.944846] EXT3 FS on sda1, internal journal
[   41.354399] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.386984] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   42.375460] No dock devices found.
[   42.735412] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[   42.735447] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x10
[   42.735449] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x12
[   42.735452] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x18
[   43.683782] apm: BIOS not found.
[   43.942673] ppdev: user-space parallel port driver
[   44.089907] audit(1211388474.233:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4981 profile="/usr/sbin/cupsd" namespace="default"
[   49.885209] Marking TSC unstable due to: cpufreq changes.
[   49.885742] Time: acpi_pm clocksource has been installed.
[  102.561596] Clocksource tsc unstable (delta = -119237055 ns)
[  102.975278] Bluetooth: Core ver 2.11
[  102.976598] input: b43-phy0 as /devices/virtual/input/input9
[  102.985753] NET: Registered protocol family 31
[  102.985763] Bluetooth: HCI device and connection manager initialized
[  102.985771] Bluetooth: HCI socket layer initialized
[  103.029606] Bluetooth: L2CAP ver 2.9
[  103.029615] Bluetooth: L2CAP socket layer initialized
[  103.141470] Bluetooth: RFCOMM socket layer initialized
[  103.143011] Bluetooth: RFCOMM TTY layer initialized
[  103.143019] Bluetooth: RFCOMM ver 1.8
[   47.551521] Registered led device: b43-phy0:tx
[   47.552096] Registered led device: b43-phy0:rx
[   47.552605] Registered led device: b43-phy0:radio
[  109.368925] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[  109.368937] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   50.217251] [fglrx] Maximum main memory to use for locked dma buffers: 1776 MBytes.
[   50.218784] [fglrx] GART Table is not in FRAME_BUFFER range 
[   50.218792] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   50.218795] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
[   50.637723] [fglrx] interrupt source 20008000 successfully enabled
[   50.637729] [fglrx] enable ID = 0x00000004
[   50.638865] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   62.068390] hda-intel: Invalid position buffer, using LPIB read method instead.
[  134.268377] NET: Registered protocol family 10
[  134.270130] lo: Disabled Privacy Extensions
[  134.272995] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  134.275318] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   77.490143] NET: Registered protocol family 17
[   69.844473] wlan0: Initial auth_alg=0
[   69.844480] wlan0: authenticate with AP 00:40:05:49:14:3d
[   69.848372] wlan0: RX authentication from 00:40:05:49:14:3d (alg=0 transaction=2 status=0)
[   69.848375] wlan0: authenticated
[   69.848378] wlan0: associate with AP 00:40:05:49:14:3d
[   69.852369] wlan0: RX AssocResp from 00:40:05:49:14:3d (capab=0x51 status=0 aid=3)
[   69.852372] wlan0: associated
[   69.853451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   86.903647] wlan0: no IPv6 routers present
[  399.391214] usb 1-1: new low speed USB device using ohci_hcd and address 2
[  178.027658] usb 1-1: configuration #1 chosen from 1 choice
[  178.758928] usbcore: registered new interface driver hiddev
[  178.904754] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input10
[  178.962016] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1
[  179.277859] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.1/input/input11
[  179.312810] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-1
[  179.313941] usbcore: registered new interface driver usbhid
[  179.314079] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  180.528761] irq 10: nobody cared (try booting with the "irqpoll" option)
[  180.528771] Pid: 5673, comm: gnome-screensav Tainted: P        2.6.24-16-generic #1
[  180.528795]  [<c0164924>] __report_bad_irq+0x24/0x80
[  180.528810]  [<c0164bfb>] note_interrupt+0x27b/0x2c0
[  180.528817]  [<f8d59e64>] azx_interrupt+0x14/0xf0 [snd_hda_intel]
[  180.528849]  [<c0163e20>] handle_IRQ_event+0x30/0x60
[  180.528862]  [<c01657c1>] handle_level_irq+0x91/0xf0
[  180.528873]  [<c0106f1b>] do_IRQ+0x3b/0x70
[  180.528890]  [<c0105413>] common_interrupt+0x23/0x30
[  180.528925]  =======================
[  180.528926] handlers:
[  180.528928] [<f8a7dbe0>] (sdhci_irq+0x0/0x5c0 [sdhci])
[  180.528934] [<f8d59e50>] (azx_interrupt+0x0/0xf0 [snd_hda_intel])
[  180.528952] [<f888e310>] (b44_interrupt+0x0/0x100 [b44])
[  180.528961] Disabling IRQ #10
[ 1108.949273] usb 1-1: USB disconnect, address 2
[ 1111.116680] usb 2-1: new low speed USB device using ohci_hcd and address 2
[ 1111.337939] usb 2-1: configuration #1 chosen from 1 choice
[ 1111.388159] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb2/2-1/2-1:1.0/input/input12
[ 1111.420663] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-1
[ 1111.431980] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb2/2-1/2-1:1.1/input/input13
[ 1111.452774] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.1-1
[ 1126.582008] usb 2-1: USB disconnect, address 2
[ 1129.977322] usb 1-1: new low speed USB device using ohci_hcd and address 3
[ 1131.586095] usb 1-1: configuration #1 chosen from 1 choice
[ 1132.712553] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input14
[ 1132.736765] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1
[  504.136186] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.1/input/input15
[  504.163090] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-1
[ 1276.083669] usb 1-1: USB disconnect, address 3
[ 1282.778098] usb 1-1: new low speed USB device using ohci_hcd and address 4
[ 1284.317722] usb 1-1: configuration #1 chosen from 1 choice
[  570.965963] input: Logitech USB-PS/2 Mouse M-BA47 as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input16
[  570.992614] input,hidraw0: USB HID v1.00 Mouse [Logitech USB-PS/2 Mouse M-BA47] on usb-0000:00:13.0-1
[ 1300.743035] usb 1-1: USB disconnect, address 4
[ 1301.923043] usb 2-1: new low speed USB device using ohci_hcd and address 3
[ 1302.184305] usb 2-1: configuration #1 chosen from 1 choice
[ 1302.199263] input: Logitech USB-PS/2 Mouse M-BA47 as /devices/pci0000:00/0000:00:13.1/usb2/2-1/2-1:1.0/input/input17
[ 1302.226782] input,hidraw0: USB HID v1.00 Mouse [Logitech USB-PS/2 Mouse M-BA47] on usb-0000:00:13.1-1
[ 1305.097892] usb 2-1: USB disconnect, address 3
[ 1344.270951] usb 1-1: new low speed USB device using ohci_hcd and address 5
[ 1345.562025] usb 1-1: configuration #1 chosen from 1 choice
[  598.597331] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input18
[  598.623481] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1
[  674.275582] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.1/input/input19
[  674.301800] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-1
[  738.922750] wlan0: deauthenticate(reason=3)
[ 1671.191472] wlan0: Initial auth_alg=0
[ 1671.191484] wlan0: authenticate with AP 00:40:05:49:14:3d
[ 1671.193835] wlan0: RX authentication from 00:40:05:49:14:3d (alg=0 transaction=2 status=0)
[ 1671.193843] wlan0: authenticated
[ 1671.193849] wlan0: associate with AP 00:40:05:49:14:3d
[ 1671.195812] wlan0: RX AssocResp from 00:40:05:49:14:3d (capab=0x51 status=0 aid=3)
[ 1671.195818] wlan0: associated
[ 1671.197996] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  758.607531] wlan0: no IPv6 routers present
```

---

### Post by AaronMT on 2008-05-21
Does this mean that under Ubuntu that port is a USB 1.1 port? Why would this not be a problem under Vista?

```
aaron@aaron-laptop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
aaron@aaron-laptop:~$ sudo lsusb -v | grep bcdUSB 
  bcdUSB               2.00
  bcdUSB               1.10
  bcdUSB               1.10
  bcdUSB               1.10
  bcdUSB               2.00
  bcdUSB               1.10
  bcdUSB               1.10
aaron@aaron-laptop:~$ sudo lsusb -v | grep bcdUSB | awk '{print $2}'
2.00
1.10
1.10
1.10
2.00
1.10
1.10
aaron@aaron-laptop:~$ 

```

I am fairly certain that they are all USB 2.0 ports. As this is only a problem with one USB port.

---

### Post by AaronMT on 2008-05-21
Output of **/var/log/messages** after switching ports back and forth

```
May 21 13:28:12 aaron-laptop kernel: [ 1177.743168] usb 1-1: USB disconnect, address 2
May 21 13:28:19 aaron-laptop kernel: [ 1184.229882] usb 2-1: new low speed USB device using ohci_hcd and address 3
May 21 13:28:19 aaron-laptop kernel: [ 1184.488180] usb 2-1: configuration #1 chosen from 1 choice
May 21 13:28:19 aaron-laptop kernel: [ 1184.503341] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb2/2-1/2-1:1.0/input/input14
May 21 13:28:19 aaron-laptop kernel: [ 1184.529857] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-1
May 21 13:28:19 aaron-laptop kernel: [ 1184.541133] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb2/2-1/2-1:1.1/input/input15
May 21 13:28:19 aaron-laptop kernel: [ 1184.565960] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.1-1
May 21 13:31:07 aaron-laptop kernel: [ 1447.438899] usb 2-1: USB disconnect, address 3
May 21 13:31:09 aaron-laptop kernel: [ 1449.290580] usb 1-1: new low speed USB device using ohci_hcd and address 3
May 21 13:31:10 aaron-laptop kernel: [ 1450.241535] usb 1-1: configuration #1 chosen from 1 choice
May 21 13:31:11 aaron-laptop kernel: [ 1451.125621] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input16
May 21 13:31:11 aaron-laptop kernel: [ 1451.150145] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1
May 21 13:31:12 aaron-laptop kernel: [  645.151276] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.1/input/input17
May 21 13:31:12 aaron-laptop kernel: [  645.176845] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-1

```

---

### Post by AaronMT on 2008-05-21
As well, with a device in that USB port my system will bog down and audio will freeze and loop if played.

---

### Post by AaronMT on 2008-05-21
**_Issue solved_**


I removed **nolapic and apci=off** from my startup configuration. I had these in there to remove two error notices I receive upon startup.

```
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=bfe82a56-74a0-4140-9e$

```

What an interesting problem. I knew for sure my ports are 2.0.

---

