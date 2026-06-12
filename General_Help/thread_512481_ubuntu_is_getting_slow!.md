---
title: "ubuntu is getting slow!"
date: 2007-07-29
forum: General Help
---

### Post by nate_nightroad on 2007-07-29
hi, my ubuntu 7.04 32bit is getting slow...everytime i open something(whether is app or folders) i will have to wait like 15 seconds before anything comes up....tis prob onli happen yesterday....

here is wat i did yesterday:

i updated my wesnoth thru update manager......
i installed epiphany thru Add/Remove but i dont like epiphany and i uninstalled it thru  Add/Remove and i purge it at terminal 

sudo aptitude purge epiphany

i also mount an ISO file with the following command:

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop

tat's all i did yesterday.....please advice, tis slow thing is driving me nuts and i have no problem before,everything was fine.....thanks in advanced!!!!!

---

### Post by kostkon on 2007-07-29
First, check if something hasn't terminated well and it's still running in the background eating your resources. Go to *System -> Administration -> System Monitor* and check what is running. A different way to do it would be to open a terminal and type
```
top
```

I hope this will help you somehow.

---

### Post by bettlebrox on 2007-07-29
As kostkon use top. It's possible all your memory us being used or some process has gone awry and is using too much CPU. 

By default top will sort based on CPU usages so you can see if there something using too much CPU all the time. "Shift M" will sort on Memory. Also, the first few lines will show total memory usage like this:

Mem:   1278516k total,  1228504k used,    50012k free,   381168k buffers
Swap:  1124476k total,    33808k used,  1090668k free,   306232k cached

So you can see if your using all your available.

---

### Post by nate_nightroad on 2007-07-29
thanks for the fast reply...after checking i found out tat all of the CPU usaga is close to 0%, user memory is onli 14.7%

i dint use any swap memory so is 0%

for the processes tab,all of the process is at a sleep status......

but the problem still presist...

---

### Post by kostkon on 2007-07-29
Did you restart your system? If your ISO is still mounted, try to unmount it with
```
sudo umount /media/iso
```
and see what happens.

---

### Post by nate_nightroad on 2007-07-29
i did unmount the ISO....and i tried restarting the system.....

i even tried to delete the ISO folder in /media/ but i create the ISO folder again......

---

### Post by nate_nightroad on 2007-08-06
i'm really tired of this slow response system.....is there anyway to 'repair' the system?

---

### Post by bogolisk on 2007-08-06
> **nate_nightroad said:**
> i'm really tired of this slow response system.....is there anyway to 'repair' the system?

open a terminal and
```

  tail -f /var/log/kernel

```

then do what you do normally that cause slowness. see if the kernel log shows any errors. The symptoms sound like some hw timeout (dma or interrupt).

---

### Post by nate_nightroad on 2007-08-07
it says the following :

tail: cannot open `/var/log/kernel' for reading: No such file or directory
tail: no files remaining

anymore advise?

---

### Post by kevinlyfellow on 2007-08-07
He meant
```
sudo tail -f /var/log/kern.log
```
I think

---

### Post by nate_nightroad on 2007-08-07
yeah i when into tat file and there is alot of crap,which i dont understand a thing about it....should i upload tat log file?

---

### Post by vexorian on 2007-08-07
I recommend system monitor (system\administration\System monitor" over top since it is a little easier to see what's going on.

---

### Post by nate_nightroad on 2007-08-07
i did tat already and the cpu usage is like almost 0% and memory usage is quite low......

now i did the code of sudo tail -f /var/log/kern.log and here is the code tat came out :

Aug  7 12:38:55 L-Ubuntu kernel: [   45.044346] Bluetooth: Core ver 2.11
Aug  7 12:38:55 L-Ubuntu kernel: [   45.044395] NET: Registered protocol family 31
Aug  7 12:38:55 L-Ubuntu kernel: [   45.044397] Bluetooth: HCI device and connection manager initialized
Aug  7 12:38:55 L-Ubuntu kernel: [   45.044399] Bluetooth: HCI socket layer initialized
Aug  7 12:38:55 L-Ubuntu kernel: [   45.092570] Bluetooth: L2CAP ver 2.8
Aug  7 12:38:55 L-Ubuntu kernel: [   45.092572] Bluetooth: L2CAP socket layer initialized
Aug  7 12:38:55 L-Ubuntu kernel: [   45.094193] Bluetooth: RFCOMM socket layer initialized
Aug  7 12:38:55 L-Ubuntu kernel: [   45.094199] Bluetooth: RFCOMM TTY layer initialized
Aug  7 12:38:55 L-Ubuntu kernel: [   45.094200] Bluetooth: RFCOMM ver 1.8
Aug  7 12:39:13 L-Ubuntu kernel: [   63.206839] eth0: no IPv6 routers present

---

### Post by nate_nightroad on 2007-08-07
after searching in the net about the prob,there are ppl having the same prob as i do....anyway here is the thread;

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/117483](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/117483)

anyway hope someone will work on the bug

---

### Post by gmaniac on 2007-08-07
Could you post the output of
```
sudo hdparm /dev/hda
``` 
(assuming hda is the disk your root partition is)
If you aren't using dma that's bad.

also do a ```
dmesg
``` and post the output here.

I had this problem once when my partition was formated with reiserfs and it was
near it's capacity. 

Do a df -h and see if /  has space....

---

### Post by nate_nightroad on 2007-08-07
/dev/sda2:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 104197590, start = 104197590

and

[   26.952346]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.952347]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   26.952347]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   26.952348]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   26.952350] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.952459] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   26.952462] hpet0: 3 32-bit timers, 25000000 Hz
[   26.953466] Using HPET for base-timer
[   27.032277] Calibrating delay using timer specific routine.. 5760.42 BogoMIPS (lpj=11520845)
[   27.032303] Security Framework v1.0.0 initialized
[   27.032307] SELinux:  Disabled at boot.
[   27.032317] Mount-cache hash table entries: 512
[   27.032406] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   27.032411] monitor/mwait feature present.
[   27.032412] using mwait in idle threads.
[   27.032415] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.032416] CPU: L3 cache: 4096K
[   27.032418] CPU: Physical Processor ID: 0
[   27.032419] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003140 0000e3bd 00000000 00000001
[   27.032424] Compat vDSO mapped to ffffe000.
[   27.032427] Remapping vsyscall page to ffffe000
[   27.032434] Checking 'hlt' instruction... OK.
[   27.048322] SMP alternatives: switching to UP code
[   27.048591] Early unpacking initramfs... done
[   27.242448] ACPI: Core revision 20060707
[   27.249386] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   27.253081] CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[   27.253092] SMP alternatives: switching to SMP code
[   27.253143] Booting processor 1/1 eip 3000
[   27.263897] Initializing CPU#1
[   27.343562] Calibrating delay using timer specific routine.. 5755.93 BogoMIPS (lpj=11511861)
[   27.343566] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   27.343569] monitor/mwait feature present.
[   27.343571] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.343573] CPU: L3 cache: 4096K
[   27.343574] CPU: Physical Processor ID: 0
[   27.343575] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003140 0000e3bd 00000000 00000001
[   27.344025] CPU1: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[   27.344038] Total of 2 processors activated (11516.35 BogoMIPS).
[   27.344259] ENABLING IO-APIC IRQs
[   27.344439] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   27.491225] checking TSC synchronization across 2 CPUs: passed.
[    0.003990] Brought up 2 CPUs
[    0.365779] migration_cost=95
[    0.365957] Booting paravirtualized kernel on bare hardware
[    0.366017] Time: 19:27:59  Date: 07/07/107
[    0.366034] NET: Registered protocol family 16
[    0.366087] EISA bus registered
[    0.366090] ACPI: bus type pci registered
[    0.399341] PCI: PCI BIOS revision 3.00 entry at 0xfba40, last bus=3
[    0.399342] PCI: Using configuration type 1
[    0.399343] Setting up standard PCI resources
[    0.411506] ACPI: Interpreter enabled
[    0.411507] ACPI: Using IOAPIC for interrupt routing
[    0.411933] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.411937] PCI: Probing PCI hardware (bus 00)
[    0.413220] Boot video device is 0000:01:00.0
[    0.413477] PCI: Transparent bridge - 0000:00:10.0
[    0.413507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.470182] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.472903] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.473125] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.473345] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[    0.473560] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.473774] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 *10 11 14 15)
[    0.473989] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 *11 14 15)
[    0.474207] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.474426] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.474642] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.474856] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.475077] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.475297] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.475517] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.475732] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.475948] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.476164] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.476379] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.476592] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.476806] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.477022] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.477285] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.477550] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.477814] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.478072] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.478335] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.478598] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.478858] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.479120] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.479384] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.479649] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.479912] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.480178] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.480444] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.480710] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.480973] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.481233] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.481497] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.481766] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.482033] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.482298] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.482561] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.482759] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.482766] pnp: PnP ACPI init
[    0.486281] pnp: PnP ACPI: found 12 devices
[    0.486284] PnPBIOS: Disabled by ACPI PNP
[    0.486321] PCI: Using ACPI for IRQ routing
[    0.486323] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.524303] NET: Registered protocol family 8
[    0.524305] NET: Registered protocol family 20
[    0.524590] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[    0.524592] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.524594] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.524595] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[    0.524597] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.524598] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.524803] PCI: Bridge: 0000:00:03.0
[    0.524805]   IO window: e000-efff
[    0.524807]   MEM window: f8000000-fbffffff
[    0.524809]   PREFETCH window: e0000000-efffffff
[    0.524811] PCI: Bridge: 0000:00:07.0
[    0.524813]   IO window: c000-cfff
[    0.524815]   MEM window: fdd00000-fddfffff
[    0.524817]   PREFETCH window: fdc00000-fdcfffff
[    0.524819] PCI: Bridge: 0000:00:10.0
[    0.524820]   IO window: d000-dfff
[    0.524823]   MEM window: fdf00000-fdffffff
[    0.524826]   PREFETCH window: fde00000-fdefffff
[    0.524834] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.524841] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.524848] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    0.524863] NET: Registered protocol family 2
[    0.582957] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.583032] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.583400] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.583542] TCP: Hash tables configured (established 131072 bind 65536)
[    0.583543] TCP reno registered
[    0.595052] checking if image is initramfs... it is
[    0.978041] Freeing initrd memory: 7608k freed
[    0.978396] audit: initializing netlink socket (disabled)
[    0.978408] audit(1186514879.604:1): initialized
[    0.978487] highmem bounce pool size: 64 pages
[    0.978551] VFS: Disk quotas dquot_6.5.1
[    0.978562] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.978600] io scheduler noop registered
[    0.978602] io scheduler anticipatory registered
[    0.978603] io scheduler deadline registered
[    0.978610] io scheduler cfq registered (default)
[    1.018349] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.018384] assign_interrupt_mode Found MSI capability
[    1.018387] Allocate Port Service[0000:00:03.0:pcie00]
[    1.018458] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    1.018484] assign_interrupt_mode Found MSI capability
[    1.018486] Allocate Port Service[0000:00:07.0:pcie00]
[    1.018593] isapnp: Scanning for PnP cards...
[    1.370599] isapnp: No Plug & Play device found
[    1.385950] Real Time Clock Driver v1.12ac
[    1.386081] hpet_resources: 0xfeff0000 is busy
[    1.386098] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.386205] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.386631] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.386758] mice: PS/2 mouse device common for all mice
[    1.387139] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.387245] input: Macintosh mouse button emulation as /class/input/input0
[    1.387274] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.387276] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.387461] PNP: No PS/2 controller found. Probing ports directly.
[    1.387763] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.387765] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.387825] EISA: Probing bus 0 at eisa.0
[    1.387829] Cannot allocate resource for EISA slot 1
[    1.387846] EISA: Detected 0 cards.
[    1.417843] TCP cubic registered
[    1.417848] NET: Registered protocol family 1
[    1.417863] Starting balanced_irq
[    1.417868] Using IPI No-Shortcut mode
[    1.417926] ACPI: (supports S0 S1 S3 S4 S5)
[    1.417958]   Magic number: 3:479:495
[    1.418201] Freeing unused kernel memory: 328k freed
[    1.420740] Time: tsc clocksource has been installed.
[    2.735671] Capability LSM initialized
[    2.755382] ACPI: Fan [FAN] (on)
[    2.757414] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [Nvidia] OemTableId [ASUSACPI] [20060707]
[    2.757616] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [Nvidia] OemTableId [ASUSACPI] [20060707]
[    2.757650] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.757654] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.758570] ACPI: Thermal Zone [THRM] (40 C)
[    2.997937] SCSI subsystem initialized
[    3.002179] libata version 2.20 loaded.
[    3.022508] ahci 0000:02:00.0: version 2.1
[    3.022822] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[    3.022828] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 16
[    3.029515] ieee1394: Initialized config rom entry `ip1394'
[    3.032433] usbcore: registered new interface driver usbfs
[    3.032449] usbcore: registered new interface driver hub
[    3.032462] usbcore: registered new device driver usb
[    3.065462] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.066576] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[    4.023040] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    4.023048] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    4.023050] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    4.023143] ata1: SATA max UDMA/133 cmd 0xf885c100 ctl 0x00000000 bmdma 0x00000000 irq 16
[    4.023154] scsi0 : ahci
[    4.336769] ata1: SATA link down (SStatus 0 SControl 300)
[    4.337169] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    4.337174] ACPI: PCI Interrupt 0000:03:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 17
[    4.389779] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.395081] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    4.395084] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 18
[    4.395088] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    4.395092] forcedeth: using HIGHDMA
[    4.915150] eth0: forcedeth.c: subsystem: 01043:8221 bound to 0000:00:14.0
[    4.915469] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[    4.915471] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 19
[    4.915477] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    4.915479] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    4.915572] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    4.915583] ohci_hcd 0000:00:0b.0: irq 19, io mem 0xfe02f000
[    4.973295] usb usb1: configuration #1 chosen from 1 choice
[    4.973309] hub 1-0:1.0: USB hub found
[    4.973314] hub 1-0:1.0: 8 ports detected
[    5.080009] sata_nv 0000:00:0e.0: version 3.3
[    5.080311] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[    5.080314] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 20
[    5.080325] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    5.080417] ata2: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001f800 irq 20
[    5.080438] ata3: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001f808 irq 20
[    5.080446] scsi1 : sata_nv
[    5.380759] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    5.549823] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.558995] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    5.558999] ata2.00: ATA-7: Maxtor 6V160E0, VA111630, max UDMA/133
[    5.559002] ata2.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    5.571060] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    5.571064] ata2.00: configured for UDMA/133
[    5.571071] scsi2 : sata_nv
[    5.605843] usb 1-2: configuration #1 chosen from 1 choice
[    5.666661] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001081c13]
[    5.911166] usb 1-3: new full speed USB device using ohci_hcd and address 3
[    6.035962] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.045136] ata3.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[    6.045140] ata3.00: ATA-7: Maxtor 6V300F0, VA111630, max UDMA/133
[    6.045142] ata3.00: 586114704 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    6.057193] ata3.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[    6.057197] ata3.00: configured for UDMA/133
[    6.057304] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6V160E0   VA11 PQ: 0 ANSI: 5
[    6.057632] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6V300F0   VA11 PQ: 0 ANSI: 5
[    6.058123] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[    6.058128] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 21
[    6.058140] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    6.058164] ata4: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001f300 irq 21
[    6.058188] ata5: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001f308 irq 21
[    6.058199] scsi3 : sata_nv
[    6.121658] usb 1-3: configuration #1 chosen from 1 choice
[    6.124627] hub 1-3:1.0: USB hub found
[    6.127597] hub 1-3:1.0: 4 ports detected
[    6.526460] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.550603] usb 1-4: new full speed USB device using ohci_hcd and address 4
[    6.576763] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[    6.576767] ata4.00: ATA-7: ST3500630AS, 3.AAE, max UDMA/133
[    6.576769] ata4.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    6.643245] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[    6.643249] ata4.00: configured for UDMA/133
[    6.643256] scsi4 : sata_nv
[    6.774161] usb 1-4: configuration #1 chosen from 1 choice
[    6.952835] ata5: SATA link down (SStatus 0 SControl 300)
[    6.963237] ATA: abnormal status 0x7F on port 0x00010967
[    6.963310] scsi 3:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    6.964059] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[    6.964061] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 18
[    6.964068] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    6.964070] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    6.964140] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    6.964157] ehci_hcd 0000:00:0b.1: debug port 1
[    6.964160] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[    6.964167] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xfe02e000
[    6.964172] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.964407] usb usb2: configuration #1 chosen from 1 choice
[    6.964422] hub 2-0:1.0: USB hub found
[    6.964427] hub 2-0:1.0: 8 ports detected
[    7.018559] hub 1-3:1.0: hub_port_status failed (err = -62)
[    7.021549] hub 1-3:1.0: hub_port_status failed (err = -62)
[    7.024542] hub 1-3:1.0: hub_port_status failed (err = -62)
[    7.027535] hub 1-3:1.0: hub_port_status failed (err = -62)
[    7.027543] usb 1-2: USB disconnect, address 2
[    7.070511] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    7.070523] NFORCE-MCP51: chipset revision 161
[    7.070524] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    7.070529] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[    7.070534]     ide0: BM-DMA at 0xfd00-0xfd07, BIOS settings: hda:DMA, hdb:DMA
[    7.070540]     ide1: BM-DMA at 0xfd08-0xfd0f, BIOS settings: hdc:DMA, hdd:DMA
[    7.070544] Probing IDE interface ide0...
[    7.085036] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    7.085044] sda: Write Protect is off
[    7.085045] sda: Mode Sense: 00 3a 00 00
[    7.085053] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.085082] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    7.085087] sda: Write Protect is off
[    7.085088] sda: Mode Sense: 00 3a 00 00
[    7.085096] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.085098]  sda: sda1 sda2
[    7.104343] sd 1:0:0:0: Attached scsi disk sda
[    7.104380] SCSI device sdb: 586114704 512-byte hdwr sectors (300091 MB)
[    7.104388] sdb: Write Protect is off
[    7.104389] sdb: Mode Sense: 00 3a 00 00
[    7.104402] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.104431] SCSI device sdb: 586114704 512-byte hdwr sectors (300091 MB)
[    7.104438] sdb: Write Protect is off
[    7.104439] sdb: Mode Sense: 00 3a 00 00
[    7.104616] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.104617]  sdb: sdb1 < sdb5 >
[    7.125290] sd 2:0:0:0: Attached scsi disk sdb
[    7.125322] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[    7.125330] sdc: Write Protect is off
[    7.125331] sdc: Mode Sense: 00 3a 00 00
[    7.125343] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.125373] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[    7.125380] sdc: Write Protect is off
[    7.125382] sdc: Mode Sense: 00 3a 00 00
[    7.125395] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.125397]  sdc: sdc1 < sdc5 >
[    7.140223] sd 3:0:0:0: Attached scsi disk sdc
[    7.143002] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    7.143080] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    7.143154] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    7.153805] usb 1-3: USB disconnect, address 3
[    7.286955] usb 1-4: USB disconnect, address 4
[    7.348719] kjournald starting.  Commit interval 5 seconds
[    7.348727] EXT3-fs: mounted filesystem with ordered data mode.
[    7.806081] hda: SONY DVD RW DRU-810A, ATAPI CD/DVD-ROM drive
[    8.280904] usbcore: registered new interface driver hiddev
[    8.582947] usb 1-2: new low speed USB device using ohci_hcd and address 6
[    8.591157] hdb: TSSTcorp CDW/DVD SH-M522C, ATAPI CD/DVD-ROM drive
[    8.648806] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    8.666748] Probing IDE interface ide1...
[    8.792533] usb 1-2: configuration #1 chosen from 1 choice
[    9.098685] usb 1-3: new full speed USB device using ohci_hcd and address 7
[    9.293383] usb 1-3: configuration #1 chosen from 1 choice
[    9.296350] hub 1-3:1.0: USB hub found
[    9.299326] hub 1-3:1.0: 4 ports detected
[    9.727160] usb 1-4: new full speed USB device using ohci_hcd and address 8
[    9.961852] usb 1-4: configuration #1 chosen from 1 choice
[   10.271607] usb 1-7: new full speed USB device using ohci_hcd and address 9
[   10.469681] usb 1-7: configuration #1 chosen from 1 choice
[   10.491629] input: Logitech Logitech RumblePad 2 USB as /class/input/input1
[   10.491633] input: USB HID v1.10 Joystick [Logitech Logitech RumblePad 2 USB] on usb-0000:00:0b.0-2
[   10.689179] usb 1-3.1: new low speed USB device using ohci_hcd and address 10
[   10.799929] usb 1-3.1: configuration #1 chosen from 1 choice
[   11.032352] usb 1-3.4: new full speed USB device using ohci_hcd and address 11
[   11.150123] usb 1-3.4: configuration #1 chosen from 1 choice
[   11.163108] input: Logitech USB Gaming Mouse as /class/input/input2
[   11.163123] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:0b.0-4
[   11.176063] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:0b.0-4
[   11.181081] input: Gaming Keyboard as /class/input/input3
[   11.181088] input: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:0b.0-3.1
[   11.194009] input: Gaming Keyboard as /class/input/input4
[   11.194028] input,hiddev97: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:0b.0-3.1
[   11.203018] input: G11 Keyboard as /class/input/input5
[   11.203037] input,hiddev98: USB HID v1.11 Keypad [G11 Keyboard] on usb-0000:00:0b.0-3.4
[   11.203046] usbcore: registered new interface driver usbhid
[   11.203048] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   14.360978] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.374963] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.385611] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   14.385631] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   14.403883] input: PC Speaker as /class/input/input6
[   14.434965] usbcore: registered new interface driver xpad
[   14.434967] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   14.463509] Linux agpgart interface v0.102 (c) Dave Jones
[   14.492041] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   14.492046] Uniform CD-ROM driver Revision: 3.20
[   14.500796] hdb: ATAPI 52X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[   14.503617] parport: PnPBIOS parport detected.
[   14.503641] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   14.830945] nvidia: module license 'NVIDIA' taints kernel.
[   15.081891] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   15.081895] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
[   15.081901] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   15.082007] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.09  Sat May 26 00:47:07 PDT 2007
[   15.204853] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.302942] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   15.302946] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 19
[   15.302958] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   15.316110] Netfilter messages via NETLINK v0.30.
[   15.318804] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   15.512601] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   15.748207] fuse init (API version 7.8)
[   15.786607] lp0: using parport0 (interrupt-driven).
[   15.990246] EXT3 FS on sda2, internal journal
[   22.445765] NET: Registered protocol family 17
[   22.497125] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   22.554190] NTFS volume version 3.1.
[   22.578585] NTFS volume version 3.1.
[   26.807831] NET: Registered protocol family 10
[   26.807898] lo: Disabled Privacy Extensions
[   33.941560] No dock devices found.
[   33.984114] ibm_acpi: ec object not found
[   34.021665] Using specific hotkey driver
[   34.059850] input: Power Button (FF) as /class/input/input7
[   34.059866] ACPI: Power Button (FF) [PWRF]
[   34.059888] input: Power Button (CM) as /class/input/input8
[   34.059898] ACPI: Power Button (CM) [PWRB]
[   34.139530] pcc_acpi: loading...
[   37.188041] eth0: no IPv6 routers present
[   46.032183] ppdev: user-space parallel port driver
[   46.592443] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   46.592446] apm: disabled - APM is not SMP safe.
[   47.012290] Bluetooth: Core ver 2.11
[   47.012333] NET: Registered protocol family 31
[   47.012335] Bluetooth: HCI device and connection manager initialized
[   47.012337] Bluetooth: HCI socket layer initialized
[   47.026339] Bluetooth: L2CAP ver 2.8
[   47.026343] Bluetooth: L2CAP socket layer initialized
[   47.038356] Bluetooth: RFCOMM socket layer initialized
[   47.038364] Bluetooth: RFCOMM TTY layer initialized
[   47.038366] Bluetooth: RFCOMM ver 1.8
[   67.767044] eth0: no IPv6 routers present
[   90.812466] eth0: link down.
[   95.059235] eth0: link up.
[   95.060495] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  103.080903] eth0: link down.
[  104.995107] eth0: link up.
[  104.995126] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  314.500381] eth0: no IPv6 routers present

my hdd have plenty of space left

---

### Post by nate_nightroad on 2007-08-08
hey fellas, today when i disable my wired connection(LAN) via system > administration > network, the speed is increased back to normal!

but then again, when i reenable it, ubuntu become slow again...

so any advise?

---

### Post by bettlebrox on 2007-08-08
Is the ipv6 module loaded? If it is, blacklist it and see if that helps.

Also, post your /etc/network/interfaces file.

---

### Post by nate_nightroad on 2007-08-09
how do i blacklist the ipv6 module....

here is my /etc/network/interfaces:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth0

---

### Post by bettlebrox on 2007-08-09
See if the module is loaded 1st:

lsmod | grep ipv6

To blacklist it (stop it from loading) see this thread:
[http://ubuntuforums.org/showpost.php?p=1565035&postcount=8](http://ubuntuforums.org/showpost.php?p=1565035&postcount=8)

---

### Post by nate_nightroad on 2007-08-10
i already disable/blacklist ipv6 but the slowness still presist...

anymore idea and advice?

---

### Post by bettlebrox on 2007-08-10
Did you reboot after blacklisting the ipv6 module?

What is the output from the "free" command.

---

### Post by nate_nightroad on 2007-08-12
yes i did reboot after blacklisting the ipv6 module.....

here is the free command output:

             total       used       free     shared    buffers     cached
Mem:       2075068     760924    1314144          0      99600     407208
-/+ buffers/cache:     254116    1820952
Swap:            0          0          0

please advice i'm reli desperate....i reli dont wan to reformat the OS.....thanks in advanced

i was thinking bout uninstalling my LAN driver and purging all of the driver's setting then i install a fresh new driver...will tis help?

---

### Post by nate_nightroad on 2007-08-17
so help from expert as well.....

now i'm depressed

---

