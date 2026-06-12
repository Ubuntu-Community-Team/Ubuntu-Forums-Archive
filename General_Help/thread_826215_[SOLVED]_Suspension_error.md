---
title: "[SOLVED] Suspension error"
date: 2008-06-11
forum: General Help
---

### Post by N4zgu1 on 2008-06-11
I have ubuntu 8.04 and I have a problem with suspending my laptop each time that I try to resume it I get a message like this




[149.178805] drm_sysfs_suspend

[0.729671] i8042 aux 00:09 activation failed



The numbers betwen the brackets change each time
Can anybody help me?

---

### Post by ajmorris on 2008-06-11
> **N4zgu1 said:**
> I have ubuntu 8.04 and I have a problem with suspending my laptop each time that I try to resume it I get a message like this




[149.178805] drm_sysfs_suspend

[0.729671] i8042 aux 00:09 activation failed



The numbers betwen the brackets change each time
Can anybody help me?

Hi there, 
can you please post the output of the following commands:
```
sudo lspci
```
```
less /var/log/syslog
```
```
sudo dmesg
```

AJ

---

### Post by N4zgu1 on 2008-06-12
Here is the output:

sudo lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```









less /var/log/syslog
```
Jun  9 09:04:15 carlos-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun  9 09:04:15 carlos-laptop anacron[5522]: Job `cron.daily' terminated
Jun  9 09:04:15 carlos-laptop anacron[5522]: Normal exit (1 job run)
Jun  9 09:12:30 carlos-laptop kernel: [ 2552.304106] sky2 eth0: Link is down.
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.123847] CPU0 attaching NULL sched-domain.
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.123854] CPU1 attaching NULL sched-domain.
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154776] CPU0 attaching sched-domain:
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154783]  domain 0: span 03
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154785]   groups: 01 02
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154788]   domain 1: span 03
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154790]    groups: 03
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154793] CPU1 attaching sched-domain:
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154794]  domain 0: span 03
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154796]   groups: 02 01
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154801]   domain 1: span 03
Jun  9 09:12:31 carlos-laptop kernel: [ 2553.154802]    groups: 03
Jun  9 09:12:32 carlos-laptop pulseaudio[6275]: module-alsa-sink.c: Error opening PCM device front:0: Dispositivo ó recurso ocupado
Jun  9 09:17:01 carlos-laptop /USR/SBIN/CRON[9011]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  9 09:21:57 carlos-laptop NetworkManager: <info>  Going to sleep. 
Jun  9 09:21:58 carlos-laptop kernel: [ 3119.331518] sky2 eth0: disabling interface
Jun  9 09:21:58 carlos-laptop avahi-daemon[5092]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  9 09:21:58 carlos-laptop avahi-daemon[5092]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.101.79.86.
Jun  9 09:21:58 carlos-laptop dhclient: receive_packet failed on eth0: Network is down
Jun  9 09:21:58 carlos-laptop NetworkManager: <debug> [1213021318.083126] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_a0_d1_78_c5_b2'). 
Jun  9 09:21:58 carlos-laptop avahi-daemon[5092]: Withdrawing address record for fe80::2a0:d1ff:fe78:c5b2 on eth0.
Jun  9 09:21:58 carlos-laptop avahi-daemon[5092]: Withdrawing address record for 10.101.79.86 on eth0.
Jun  9 09:21:58 carlos-laptop kernel: [ 3119.387626] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Jun  9 09:21:58 carlos-laptop NetworkManager: <debug> [1213021318.296868] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1b_77_28_76_e9'). 
Jun  9 09:21:58 carlos-laptop NetworkManager: <info>  Deactivating device wlan0. 
Jun  9 09:21:58 carlos-laptop kernel: [ 3119.660416] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Jun  9 09:21:58 carlos-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on wlan0: No such device 
Jun  9 09:21:58 carlos-laptop NetworkManager: <debug> [1213021318.815511] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1b_77_28_76_e9_0'). 
Jun  9 10:15:08 carlos-laptop kernel: [ 3120.882969] Syncing filesystems ... done.
Jun  9 10:15:08 carlos-laptop kernel: [ 3120.882997] PM: Preparing system for mem sleep
Jun  9 10:15:08 carlos-laptop kernel: [ 3120.882999] Freezing user space processes ... (elapsed 0.00 seconds) done.
Jun  9 10:15:08 carlos-laptop kernel: [ 3120.883733] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Jun  9 10:15:08 carlos-laptop kernel: [ 3120.982694] PM: Entering mem sleep
```






sudo dmesg



```
[   20.662294] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.662436] hpet clockevent registered
[   20.742409] Calibrating delay using timer specific routine.. 3462.08 BogoMIPS (lpj=6924176)
[   20.742428] Security Framework initialized
[   20.742433] SELinux:  Disabled at boot.
[   20.742444] AppArmor: AppArmor initialized
[   20.742447] Failure registering capabilities with primary security module.
[   20.742455] Mount-cache hash table entries: 512
[   20.742563] Initializing cgroup subsys ns
[   20.742567] Initializing cgroup subsys cpuacct
[   20.742576] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   20.742584] monitor/mwait feature present.
[   20.742585] using mwait in idle threads.
[   20.742589] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.742591] CPU: L2 cache: 2048K
[   20.742594] CPU: Physical Processor ID: 0
[   20.742595] CPU: Processor Core ID: 0
[   20.742597] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   20.742605] Compat vDSO mapped to ffffe000.
[   20.742617] Checking 'hlt' instruction... OK.
[   20.758809] SMP alternatives: switching to UP code
[   20.760484] Early unpacking initramfs... done
[   21.093103] ACPI: Core revision 20070126
[   21.093149] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.122104] CPU0: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz stepping 02
[   21.122120] SMP alternatives: switching to SMP code
[   21.122884] Booting processor 1/1 eip 3000
[   21.133118] Initializing CPU#1
[   21.210203] Calibrating delay using timer specific routine.. 3458.04 BogoMIPS (lpj=6916094)
[   21.210210] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   21.210215] monitor/mwait feature present.
[   21.210218] CPU: L1 I cache: 32K, L1 D cache: 32K
[   21.210219] CPU: L2 cache: 2048K
[   21.210222] CPU: Physical Processor ID: 0
[   21.210223] CPU: Processor Core ID: 1
[   21.210224] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   21.210819] CPU1: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz stepping 02
[   21.210841] Total of 2 processors activated (6920.13 BogoMIPS).
[   21.211040] ENABLING IO-APIC IRQs
[   21.211232] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.358257] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   21.378265] Brought up 2 CPUs
[   21.378290] CPU0 attaching sched-domain:
[   21.378292]  domain 0: span 03
[   21.378294]   groups: 01 02
[   21.378297] CPU1 attaching sched-domain:
[   21.378299]  domain 0: span 03
[   21.378300]   groups: 02 01
[   21.378562] net_namespace: 64 bytes
[   21.378570] Booting paravirtualized kernel on bare hardware
[   21.379038] Time:  9:22:38  Date: 06/12/08
[   21.379066] NET: Registered protocol family 16
[   21.379288] EISA bus registered
[   21.379293] ACPI: bus type pci registered
[   21.379496] PCI: PCI BIOS revision 2.10 entry at 0xfd604, last bus=7
[   21.379498] PCI: Using configuration type 1
[   21.379500] Setting up standard PCI resources
[   21.382423] ACPI: EC: Look up EC in DSDT
[   21.384529] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   21.385040] ACPI: Interpreter enabled
[   21.385042] ACPI: (supports S0 S3 S4 S5)
[   21.385057] ACPI: Using IOAPIC for interrupt routing
[   21.385690] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   21.411674] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[   21.411677] ACPI: EC: driver started in interrupt mode
[   21.411728] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.412605] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   21.412609] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   21.413923] PCI: Transparent bridge - 0000:00:1e.0
[   21.414022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.414313] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   21.414435] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   21.414555] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   21.414684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   21.418371] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   21.418469] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   21.418563] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   21.418657] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   21.418751] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   21.418845] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   21.418939] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   21.419032] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   21.419181] ACPI: Power Resource [FN00] (off)
[   21.419240] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.419275] pnp: PnP ACPI init
[   21.419282] ACPI: bus type pnp registered
[   21.423373] pnp: PnP ACPI: found 10 devices
[   21.423375] ACPI: ACPI bus type pnp unregistered
[   21.423379] PnPBIOS: Disabled by ACPI PNP
[   21.423650] PCI: Using ACPI for IRQ routing
[   21.423653] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.478223] NET: Registered protocol family 8
[   21.478225] NET: Registered protocol family 20
[   21.478265] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   21.478270] hpet0: 3 64-bit timers, 14318180 Hz
[   21.479305] AppArmor: AppArmor Filesystem Enabled
[   21.482092] Time: tsc clocksource has been installed.
[   21.482106] Switched to high resolution mode on CPU 0
[   21.482217] Switched to high resolution mode on CPU 1
[   21.495087] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   21.495090] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   21.495093] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   21.495096] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   21.495099] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   21.495101] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   21.495104] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   21.495107] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   21.495115] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   21.495121] system 00:06: ioport range 0x3e8-0x3ef has been reserved
[   21.495123] system 00:06: ioport range 0x400-0x401 has been reserved
[   21.495126] system 00:06: ioport range 0x680-0x69f has been reserved
[   21.495128] system 00:06: ioport range 0x800-0x80f has been reserved
[   21.495131] system 00:06: ioport range 0x1000-0x107f has been reserved
[   21.495133] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   21.495136] system 00:06: ioport range 0x1640-0x164f has been reserved
[   21.495138] system 00:06: ioport range 0xfe00-0xfe01 has been reserved
[   21.525618] PCI: Bridge: 0000:00:1c.0
[   21.525621]   IO window: 2000-2fff
[   21.525628]   MEM window: f0600000-f06fffff
[   21.525633]   PREFETCH window: f0000000-f01fffff
[   21.525639] PCI: Bridge: 0000:00:1c.1
[   21.525642]   IO window: 3000-3fff
[   21.525648]   MEM window: f0700000-f07fffff
[   21.525652]   PREFETCH window: f0200000-f03fffff
[   21.525658] PCI: Bridge: 0000:00:1c.2
[   21.525661]   IO window: 4000-4fff
[   21.525667]   MEM window: f0800000-f08fffff
[   21.525672]   PREFETCH window: f0400000-f05fffff
[   21.525686] PCI: Bus 8, cardbus bridge: 0000:07:06.0
[   21.525688]   IO window: 00001400-000014ff
[   21.525693]   IO window: 00001c00-00001cff
[   21.525698]   PREFETCH window: 50000000-53ffffff
[   21.525703]   MEM window: 54000000-57ffffff
[   21.525708] PCI: Bridge: 0000:00:1e.0
[   21.525710]   IO window: disabled.
[   21.525716]   MEM window: f0900000-f09fffff
[   21.525720]   PREFETCH window: disabled.
[   21.525752] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   21.525759] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.525784] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   21.525790] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.525815] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   21.525821] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.525836] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.525854] PCI: Enabling device 0000:07:06.0 (0000 -> 0003)
[   21.525860] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   21.525876] NET: Registered protocol family 2
[   21.570070] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.570293] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.570777] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.571026] TCP: Hash tables configured (established 131072 bind 65536)
[   21.571029] TCP reno registered
[   21.582145] checking if image is initramfs... it is
[   22.235567] Freeing initrd memory: 7321k freed
[   22.235744] Simple Boot Flag at 0x36 set to 0x1
[   22.236490] audit: initializing netlink socket (disabled)
[   22.236505] audit(1213262558.428:1): initialized
[   22.236707] highmem bounce pool size: 64 pages
[   22.238893] VFS: Disk quotas dquot_6.5.1
[   22.238972] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.239121] io scheduler noop registered
[   22.239123] io scheduler anticipatory registered
[   22.239125] io scheduler deadline registered
[   22.239137] io scheduler cfq registered (default)
[   22.239149] Boot video device is 0000:00:02.0
[   22.239362] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.239424] assign_interrupt_mode Found MSI capability
[   22.239476] Allocate Port Service[0000:00:1c.0:pcie00]
[   22.239515] Allocate Port Service[0000:00:1c.0:pcie02]
[   22.239627] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   22.239688] assign_interrupt_mode Found MSI capability
[   22.239737] Allocate Port Service[0000:00:1c.1:pcie00]
[   22.239773] Allocate Port Service[0000:00:1c.1:pcie02]
[   22.239884] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   22.239945] assign_interrupt_mode Found MSI capability
[   22.239995] Allocate Port Service[0000:00:1c.2:pcie00]
[   22.240032] Allocate Port Service[0000:00:1c.2:pcie02]
[   22.240319] isapnp: Scanning for PnP cards...
[   22.594564] isapnp: No Plug & Play device found
[   22.622251] Real Time Clock Driver v1.12ac
[   22.622504] hpet_resources: 0xfed00000 is busy
[   22.622543] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.623838] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.623908] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.624013] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.626468] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.626473] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.649667] mice: PS/2 mouse device common for all mice
[   22.649795] EISA: Probing bus 0 at eisa.0
[   22.649802] Cannot allocate resource for EISA slot 1
[   22.649805] Cannot allocate resource for EISA slot 2
[   22.649806] Cannot allocate resource for EISA slot 3
[   22.649808] Cannot allocate resource for EISA slot 4
[   22.649827] EISA: Detected 0 cards.
[   22.649831] cpuidle: using governor ladder
[   22.649832] cpuidle: using governor menu
[   22.649917] NET: Registered protocol family 1
[   22.649945] Using IPI No-Shortcut mode
[   22.649978] registered taskstats version 1
[   22.650088]   Magic number: 12:675:373
[   22.650171] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.650173] EDD information not available.
[   22.650393] Freeing unused kernel memory: 368k freed
[   22.669550] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.874081] fuse init (API version 7.9)
[   23.887451] ACPI: Transitioning device [FAN0] to D3
[   23.887454] ACPI: Transitioning device [FAN0] to D3
[   23.887457] ACPI: Fan [FAN0] (off)
[   23.893201] ACPI: SSDT 3F67C3A5, 023D (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   23.893404] ACPI: SSDT 3F67BE5E, 04C2 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   23.895299] Monitor-Mwait will be used to enter C-1 state
[   23.895302] Monitor-Mwait will be used to enter C-2 state
[   23.895305] Monitor-Mwait will be used to enter C-3 state
[   23.895449] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   23.895454] ACPI: Processor [CPU0] (supports 8 throttling states)
[   23.895686] ACPI: SSDT 3F67C5E2, 00BD (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   23.895878] ACPI: SSDT 3F67C320, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   23.896810] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   23.896815] ACPI: Processor [CPU1] (supports 8 throttling states)
[   23.900535] ACPI: Thermal Zone [TZ00] (34 C)
[   23.901220] ACPI: Invalid passive threshold
[   23.901724] ACPI: Transitioning device [FAN0] to D0
[   23.901727] ACPI: Transitioning device [FAN0] to D0
[   23.901728] ACPI: Unable to turn cooling device [f7c48708] 'on'
[   23.901731] ACPI: Thermal Zone [TZ01] (29 C)
[   24.265087] usbcore: registered new interface driver usbfs
[   24.265111] usbcore: registered new interface driver hub
[   24.265140] usbcore: registered new device driver usb
[   24.266246] USB Universal Host Controller Interface driver v3.0
[   24.266303] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   24.266314] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.266319] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.266574] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   24.266606] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   24.266731] usb usb1: configuration #1 chosen from 1 choice
[   24.266754] hub 1-0:1.0: USB hub found
[   24.266759] hub 1-0:1.0: 2 ports detected
[   24.369852] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   24.369865] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   24.369869] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   24.369893] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   24.369926] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   24.370039] usb usb2: configuration #1 chosen from 1 choice
[   24.370065] hub 2-0:1.0: USB hub found
[   24.370072] hub 2-0:1.0: 2 ports detected
[   24.372063] SCSI subsystem initialized
[   24.409749] libata version 3.00 loaded.
[   24.473768] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   24.473786] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   24.473792] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   24.473815] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   24.473850] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   24.473966] usb usb3: configuration #1 chosen from 1 choice
[   24.473991] hub 3-0:1.0: USB hub found
[   24.473998] hub 3-0:1.0: 2 ports detected
[   24.577743] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   24.577756] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   24.577760] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   24.577786] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   24.577819] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   24.577939] usb usb4: configuration #1 chosen from 1 choice
[   24.577963] hub 4-0:1.0: USB hub found
[   24.577968] hub 4-0:1.0: 2 ports detected
[   24.681738] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 16
[   24.681822] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   24.681835] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.681839] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.681864] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   24.685791] ehci_hcd 0000:00:1d.7: debug port 1
[   24.685797] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.685804] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0d44000
[   24.701555] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.701665] usb usb5: configuration #1 chosen from 1 choice
[   24.701689] hub 5-0:1.0: USB hub found
[   24.701695] hub 5-0:1.0: 8 ports detected
[   24.731534] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0905000-f09057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   24.809000] ata_piix 0000:00:1f.2: version 2.12
[   24.809010] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   24.960519] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   24.960574] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.960687] scsi0 : ata_piix
[   24.960882] scsi1 : ata_piix
[   24.961714] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   24.961717] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   25.124942] ata1.00: ATA-7: TOSHIBA MK1237GSX, DL130M, max UDMA/100
[   25.124951] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.133912] ata1.00: configured for UDMA/100
[   25.304281] Clocksource tsc unstable (delta = -6596695882 ns)
[   25.308661] Time: hpet clocksource has been installed.
[   25.324197] usb 5-8: new high speed USB device using ehci_hcd and address 3
[   25.349030] ata2.00: ATAPI: PIONEER DVD-RW DVR-K17LF, 4.53, max UDMA/33
[   25.466358] usb 5-8: configuration #1 chosen from 1 choice
[   25.537141] ata2.00: configured for UDMA/33
[   25.537325] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL13 PQ: 0 ANSI: 5
[   25.547007] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW DVR-K17LF 4.53 PQ: 0 ANSI: 5
[   25.556475] Driver 'sd' needs updating - please use bus_type methods
[   25.556547] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   25.556559] sd 0:0:0:0: [sda] Write Protect is off
[   25.556561] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.556578] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.556628] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   25.556638] sd 0:0:0:0: [sda] Write Protect is off
[   25.556641] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.556657] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.556660]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   25.593380]  sda1 sda2 sda3 < sda5 sda6 >
[   25.639695] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.644745] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.644764] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   25.692045] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.692053] Uniform CD-ROM driver Revision: 3.20
[   25.692155] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   25.708938] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   25.884221] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d178c5b2]
[   25.885884] usb 3-2: configuration #1 chosen from 1 choice
[   26.013137] Attempting manual resume
[   26.013141] swsusp: Resume From Partition 8:6
[   26.013142] PM: Checking swsusp image.
[   26.013378] PM: Resume from disk failed.
[   26.048086] kjournald starting.  Commit interval 5 seconds
[   26.048109] EXT3-fs: mounted filesystem with ordered data mode.
[   36.436989] Linux agpgart interface v0.102
[   36.501124] agpgart: Detected an Intel 945GM Chipset.
[   36.502194] agpgart: Detected 7932K stolen memory.
[   36.519403] agpgart: AGP aperture is 256M @ 0xd0000000
[   36.565251] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.613296] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.692167] intel_rng: FWH not detected
[   36.775590] input: Power Button (FF) as /devices/virtual/input/input2
[   36.784493] ACPI: Battery Slot [BAT0] (battery present)
[   36.792079] ACPI: Power Button (FF) [PWRF]
[   36.792186] input: Lid Switch as /devices/virtual/input/input3
[   36.792246] ACPI: Lid Switch [LID]
[   36.792309] input: Power Button (CM) as /devices/virtual/input/input4
[   36.816088] ACPI: Power Button (CM) [PWRB]
[   36.937663] ACPI: AC Adapter [ADP0] (off-line)
[   37.168045] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5
[   37.195890] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   37.197951] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
[   37.199783] iTCO_vendor_support: vendor-support=0
[   37.215971] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   37.216063] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   37.216101] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   37.227882] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   37.366515] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   37.366530] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   37.366565] sky2 0000:02:00.0: v1.20 addr 0xf0600000 irq 17 Yukon-FE (0xb7) rev 3
[   37.366997] sky2 eth0: addr 00:a0:d1:78:c5:b2
[   37.801888] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[   37.891317] Yenta: CardBus bridge found at 0000:07:06.0 [1179:ff10]
[   37.891341] Yenta: Enabling burst memory read transactions
[   37.891347] Yenta: Using CSCINT to route CSC interrupts to PCI
[   37.891349] Yenta: Routing CardBus interrupts to PCI
[   37.891356] Yenta TI: socket 0000:07:06.0, mfunc 0x01a01b22, devctl 0x66
[   37.930660] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   37.930664] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   37.987541] sdhci: Secure Digital Host Controller Interface driver
[   37.987546] sdhci: Copyright(c) Pierre Ossman
[   38.120281] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   38.120287] Socket status: 30000006
[   38.120289] Yenta: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[   38.120295] pcmcia: parent PCI bridge Memory window: 0xf0900000 - 0xf09fffff
[   38.151785] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   38.151802] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   38.151829] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   38.270746] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   38.301297] Linux video capture interface: v2.00
[   38.338825] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   38.340878] usbcore: registered new interface driver uvcvideo
[   38.340882] USB Video Class driver (v0.1.0)
[   38.903304] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x82e0b1, caps: 0xb04711/0xe0440d
[   38.903312] synaptics: Toshiba Satellite A205 detected, limiting rate to 40pps.
[   38.938388] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   38.977749] sky2 eth0: enabling interface
[   39.133595] sdhci: SDHCI controller found at 0000:07:06.3 [104c:803c] (rev 0)
[   39.133621] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[   39.133701] mmc0: SDHCI at 0xf0905800 irq 18 DMA
[   39.134064] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   39.134084] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   39.178915] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   39.179389] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   39.340957] cs: IO port probe 0x100-0x3af: clean.
[   39.343055] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   39.343877] cs: IO port probe 0x820-0x8ff: clean.
[   39.344587] cs: IO port probe 0xc00-0xcf7: clean.
[   39.345470] cs: IO port probe 0xa00-0xaff: clean.
[   39.511718] lp: driver loaded but no devices found
[   39.615857] Adding 3004112k swap on /dev/sda6.  Priority:-1 extents:1 across:3004112k
[   39.637566] EXT3 FS on sda5, internal journal
[   40.382715] NET: Registered protocol family 17
[   40.402495] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.681137] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   40.841058] No dock devices found.
[   41.837189] apm: BIOS not found.
[   41.989141] ppdev: user-space parallel port driver
[   42.185306] audit(1213280584.808:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5086 profile="/usr/sbin/cupsd" namespace="default"
[   43.717975] Bluetooth: Core ver 2.11
[   43.718136] NET: Registered protocol family 31
[   43.718141] Bluetooth: HCI device and connection manager initialized
[   43.718149] Bluetooth: HCI socket layer initialized
[   43.869552] Bluetooth: L2CAP ver 2.9
[   43.869560] Bluetooth: L2CAP socket layer initialized
[   43.875814] Bluetooth: RFCOMM socket layer initialized
[   43.875834] Bluetooth: RFCOMM TTY layer initialized
[   43.875838] Bluetooth: RFCOMM ver 1.8
[   44.057508] NET: Registered protocol family 10
[   44.058151] lo: Disabled Privacy Extensions
[   44.060457] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.863914] [drm] Initialized drm 1.1.0 20060810
[   47.867416] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   47.867428] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   47.867508] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   54.507615] eth0: no IPv6 routers present
[   83.693990] CPU0 attaching NULL sched-domain.
[   83.694002] CPU1 attaching NULL sched-domain.
[   83.706680] CPU0 attaching sched-domain:
[   83.706692]  domain 0: span 03
[   83.706696]   groups: 01 02
[   83.706703]   domain 1: span 03
[   83.706707]    groups: 03
[   83.706712] CPU1 attaching sched-domain:
[   83.706715]  domain 0: span 03
[   83.706719]   groups: 02 01
[   83.706728]   domain 1: span 03
[   83.706732]    groups: 03
```

---

### Post by ajmorris on 2008-06-12
hmm, there are no errors in syslog about the resume... odd, did you less /var/log/syslog as root? i dont think you can see any of the file without root...

Also, just to clarify, are you trying to suspend to mem (standby) or suspend to disk (hibernate)

Also, could you try this for standby:
 ```
sudo -i
echo -n "mem" > /sys/power/state

```

and post any errors you get in the terminal or upon coming out of standby after doing this

AJ

---

### Post by N4zgu1 on 2008-06-12
Maybe you didn't see any errors because I didn't suspend my laptop the day I executed the commands here is the output again:


sudo lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```


less /var/log/syslog


```
Jun 12 09:49:52 carlos-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 12 09:49:52 carlos-laptop anacron[7031]: Job `cron.daily' terminated
Jun 12 09:52:28 carlos-laptop anacron[7031]: Job `cron.weekly' started
Jun 12 09:52:28 carlos-laptop anacron[8108]: Updated timestamp for job `cron.weekly' to 2008-06-12
Jun 12 09:52:30 carlos-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 12 09:52:30 carlos-laptop anacron[7031]: Job `cron.weekly' terminated
Jun 12 09:52:30 carlos-laptop anacron[7031]: Normal exit (2 jobs run)
Jun 12 09:56:34 carlos-laptop init: tty4 main process (4590) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty5 main process (4591) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty2 main process (4593) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty6 main process (4597) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty1 main process (5617) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty3 main process (4596) killed by TERM signal
Jun 12 09:56:34 carlos-laptop gdm[5445]: WARNING: servicio principal: Se obtuvo SIGABRT. Algo ha ido muy mal. ¡Nos caemos! 
Jun 12 09:56:34 carlos-laptop gdm[5445]: GLib-CRITICAL: g_hash_table_lookup_exte/var/log/syslog 
```


sudo dmesg


```
[    0.630128] CPU: Physical Processor ID: 0
[    0.630129] CPU: Processor Core ID: 1
[    0.630130] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001 00000000
[    0.630696] CPU1: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz stepping 02
[    0.630745] CPU0 attaching sched-domain:
[    0.630748]  domain 0: span 03
[    0.630750]   groups: 01 02
[    0.630752]   domain 1: span 03
[    0.630754]    groups: 03
[    0.630756] CPU1 attaching sched-domain:
[    0.630757]  domain 0: span 03
[    0.630758]   groups: 02 01
[    0.630761]   domain 1: span 03
[    0.630762]    groups: 03
[    0.631159] CPU1 is up
[    0.634349] APIC error on CPU1: 00(40)
[    0.634351] APIC error on CPU0: 00(40)
[    0.634730] Switched to high resolution mode on CPU 1
[    0.693866] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 10b)
[    0.693881] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
[    0.711031] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900007)
[    0.711551] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 10)
[    0.711563] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100006, writing 100002)
[    0.711600] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[    0.711614] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[    0.711652] PM: Writing back config space on device 0000:00:1c.0 at offset f (was 40100, writing 4010b)
[    0.711672] PM: Writing back config space on device 0000:00:1c.0 at offset 9 (was 10001, writing f011f001)
[    0.711681] PM: Writing back config space on device 0000:00:1c.0 at offset 8 (was 0, writing f060f060)
[    0.711691] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20000000, writing 20002020)
[    0.711700] PM: Writing back config space on device 0000:00:1c.0 at offset 6 (was 0, writing 20200)
[    0.711713] PM: Writing back config space on device 0000:00:1c.0 at offset 3 (was 810000, writing 810010)
[    0.711725] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100000, writing 100407)
[    0.711787] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.711799] PM: Writing back config space on device 0000:00:1c.1 at offset f (was 40200, writing 4020b)
[    0.711813] PM: Writing back config space on device 0000:00:1c.1 at offset 9 (was 10001, writing f031f021)
[    0.711818] PM: Writing back config space on device 0000:00:1c.1 at offset 8 (was 0, writing f070f070)
[    0.711824] PM: Writing back config space on device 0000:00:1c.1 at offset 7 (was 20000000, writing 20003030)
[    0.711834] PM: Writing back config space on device 0000:00:1c.1 at offset 3 (was 810000, writing 810010)
[    0.711841] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100000, writing 100407)
[    0.711883] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.711895] PM: Writing back config space on device 0000:00:1c.2 at offset f (was 40300, writing 4030a)
[    0.711912] PM: Writing back config space on device 0000:00:1c.2 at offset 6 (was 0, writing 60500)
[    0.711921] PM: Writing back config space on device 0000:00:1c.2 at offset 3 (was 810000, writing 810010)
[    0.711928] PM: Writing back config space on device 0000:00:1c.2 at offset 1 (was 100007, writing 100407)
[    0.711970] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.711979] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    0.711985] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    0.712040] usb usb1: root hub lost power or was reset
[    0.712061] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    0.712067] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    0.712120] usb usb2: root hub lost power or was reset
[    0.712139] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.712144] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    0.712198] usb usb3: root hub lost power or was reset
[    0.712246] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    0.712253] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    0.712313] usb usb4: root hub lost power or was reset
[    0.717679] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    0.717691] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    0.717807] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 10001, writing 1fff1)
[    0.717816] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was 0, writing f090f090)
[    0.717825] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 22800000, writing 228000f0)
[    0.717835] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 38070700, writing 380b0700)
[    0.717853] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100007)
[    0.717885] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.718072] PM: Writing back config space on device 0000:00:1f.2 at offset f (was 200, writing 2ff)
[    0.718109] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00005, writing 2b80005)
[    0.718137] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    0.718147] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    0.718249] PM: Writing back config space on device 0000:02:00.0 at offset f (was 100, writing 10b)
[    0.718289] PM: Writing back config space on device 0000:02:00.0 at offset 6 (was 1, writing 2001)
[    0.718307] PM: Writing back config space on device 0000:02:00.0 at offset 4 (was 4, writing f0600004)
[    0.718327] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 10)
[    0.718338] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 100000, writing 100003)
[    0.718426] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10b)
[    0.718498] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 0, writing f0700000)
[    0.718514] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 10)
[    0.718533] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100002)
[    0.718616] PM: Writing back config space on device 0000:07:06.0 at offset f (was 34001ff, writing 5c001ff)
[    0.718622] PM: Writing back config space on device 0000:07:06.0 at offset e (was 0, writing 1cfc)
[    0.718631] PM: Writing back config space on device 0000:07:06.0 at offset d (was 0, writing 1c00)
[    0.718638] PM: Writing back config space on device 0000:07:06.0 at offset c (was 0, writing 14fc)
[    0.718644] PM: Writing back config space on device 0000:07:06.0 at offset b (was 0, writing 1400)
[    0.718650] PM: Writing back config space on device 0000:07:06.0 at offset a (was 0, writing 57fff000)
[    0.718656] PM: Writing back config space on device 0000:07:06.0 at offset 9 (was 0, writing 54000000)
[    0.718662] PM: Writing back config space on device 0000:07:06.0 at offset 8 (was 0, writing 53fff000)
[    0.718668] PM: Writing back config space on device 0000:07:06.0 at offset 7 (was 0, writing 50000000)
[    0.718675] PM: Writing back config space on device 0000:07:06.0 at offset 6 (was 0, writing b00b0807)
[    0.718684] PM: Writing back config space on device 0000:07:06.0 at offset 4 (was 0, writing f0906000)
[    0.718692] PM: Writing back config space on device 0000:07:06.0 at offset 3 (was 824000, writing 82a820)
[    0.718701] PM: Writing back config space on device 0000:07:06.0 at offset 1 (was 2100000, writing 2100007)
[    0.723345] PM: Writing back config space on device 0000:07:06.1 at offset f (was 4020200, writing 402020b)
[    0.723378] PM: Writing back config space on device 0000:07:06.1 at offset 5 (was 0, writing f0900000)
[    0.773080] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0905000-f09057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    0.774081] PM: Writing back config space on device 0000:07:06.2 at offset f (was 40701ff, writing 407010a)
[    0.774115] PM: Writing back config space on device 0000:07:06.2 at offset 4 (was 0, writing f0904000)
[    0.774130] PM: Writing back config space on device 0000:07:06.2 at offset 1 (was 2100000, writing 2100006)
[    0.774162] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[    0.774425] PM: Writing back config space on device 0000:07:06.3 at offset f (was 40701ff, writing 407010a)
[    0.774459] PM: Writing back config space on device 0000:07:06.3 at offset 4 (was 0, writing f0905800)
[    0.774473] PM: Writing back config space on device 0000:07:06.3 at offset 1 (was 2100000, writing 2100006)
[    0.774502] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[    0.774553] i8042 aux 00:09: activation failed
[    0.827304] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    0.827306] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[    0.835503] ata2.00: configured for UDMA/33
[    0.882842] sd 0:0:0:0: [sda] Starting disk
[    0.960031] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    0.960034] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    0.961950] ata1.00: configured for UDMA/100
[    0.963889] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    0.963924] sd 0:0:0:0: [sda] Write Protect is off
[    0.963929] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.964007] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.964695] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[    0.966187] PM: Finishing wakeup.
[    0.966189] Restarting tasks ... <6>usb 3-2: USB disconnect, address 3
[    0.992278] done.
[    1.112233] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[    1.112244] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[    1.112383] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[    1.112411] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    1.112439] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[    1.182570] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[    1.182613] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    1.182690] sky2 0000:02:00.0: v1.20 addr 0xf0600000 irq 17 Yukon-FE (0xb7) rev 3
[    1.187569] sky2 eth0: addr 00:a0:d1:78:c5:b2
[    1.201690] sky2 eth0: enabling interface
[    1.206180] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    1.220814] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    1.224017] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[    1.248547] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    1.288168] sky2 eth0: disabling interface
[    1.315141] usb 5-8: USB disconnect, address 5
[    1.317319] sky2 eth0: enabling interface
[    1.324256] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    1.371031] usb 5-8: new high speed USB device using ehci_hcd and address 7
[    1.517435] usb 5-8: configuration #1 chosen from 1 choice
[    1.517766] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[    1.758741] usb 3-2: new full speed USB device using uhci_hcd and address 4
[    1.931137] usb 3-2: configuration #1 chosen from 1 choice
[    3.001304] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[    3.006292] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    8.686314] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.204574] CPU0 attaching NULL sched-domain.
[   12.204581] CPU1 attaching NULL sched-domain.
[   12.222778] CPU0 attaching sched-domain:
[   12.222789]  domain 0: span 03
[   12.222794]   groups: 01 02
[   12.222801] CPU1 attaching sched-domain:
[   12.222805]  domain 0: span 03
[   12.222808]   groups: 02 01
[   13.401117] eth0: no IPv6 routers present
[   27.666320] sky2 eth0: disabling interface
[   27.970309] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[   28.211521] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   29.675332] Syncing filesystems ... done.
[   29.675359] PM: Preparing system for mem sleep
[   29.675362] Freezing user space processes ... (elapsed 0.00 seconds) done.
[   29.676069] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[   29.676118] PM: Entering mem sleep
[   29.676120] Suspending console(s)
[   29.693545] drm_sysfs_suspend
[   29.694064] ACPI: PCI interrupt for device 0000:00:02.0 disabled
[   29.696038] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[   29.707491] sd 0:0:0:0: [sda] Stopping disk
[   29.726676] ACPI handle has no context!
[   29.726743] ACPI handle has no context!
[   29.726765] ACPI: PCI interrupt for device 0000:07:06.3 disabled
[   29.726773] ACPI handle has no context!
[   29.726941] ACPI handle has no context!
[   29.726965] ACPI: PCI interrupt for device 0000:07:06.2 disabled
[   29.726975] ACPI handle has no context!
[   29.727308] ACPI handle has no context!
[   29.728186] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   29.728478] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[   29.728710] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[   29.728761] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[   29.728812] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[   29.728864] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[   29.729451] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[   29.739734] Disabling non-boot CPUs ...
[   29.739753] CPU0 attaching NULL sched-domain.
[   29.739754] CPU1 attaching NULL sched-domain.
[   29.849612] CPU 1 is now offline
[   29.849615] SMP alternatives: switching to UP code
[   29.851038] CPU0 attaching sched-domain:
[   29.851041]  domain 0: span 01
[   29.851042]   groups: 01
[   29.851224] CPU1 is down
[    0.463011] Back to C!
[    0.463447] Enabling non-boot CPUs ...
[    0.463514] CPU0 attaching NULL sched-domain.
[    0.473641] SMP alternatives: switching to SMP code
[    0.474784] Booting processor 1/1 eip 3000
[    0.484981] Initializing CPU#1
[    0.565513] Calibrating delay using timer specific routine.. 3457.87 BogoMIPS (lpj=6915748)
[    0.565521] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001 00000000
[    0.565526] monitor/mwait feature present.
[    0.565529] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.565531] CPU: L2 cache: 2048K
[    0.565533] CPU: Physical Processor ID: 0
[    0.565534] CPU: Processor Core ID: 1
[    0.565536] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001 00000000
[    0.566098] CPU1: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz stepping 02
[    0.566144] CPU0 attaching sched-domain:
[    0.566147]  domain 0: span 03
[    0.566148]   groups: 01 02
[    0.566151] CPU1 attaching sched-domain:
[    0.566152]  domain 0: span 03
[    0.566154]   groups: 02 01
[    0.566490] CPU1 is up
[    0.570047] APIC error on CPU1: 00(40)
[    0.570053] APIC error on CPU0: 00(40)
[    0.570380] Switched to high resolution mode on CPU 1
[    0.629121] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 10b)
[    0.629135] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
[    0.646269] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900007)
[    0.648146] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 10)
[    0.648157] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100006, writing 100002)
[    0.648195] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[    0.648209] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[    0.648249] PM: Writing back config space on device 0000:00:1c.0 at offset f (was 40100, writing 4010b)
[    0.648269] PM: Writing back config space on device 0000:00:1c.0 at offset 9 (was 10001, writing f011f001)
[    0.648278] PM: Writing back config space on device 0000:00:1c.0 at offset 8 (was 0, writing f060f060)
[    0.648287] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20000000, writing 2020)
[    0.648297] PM: Writing back config space on device 0000:00:1c.0 at offset 6 (was 0, writing 20200)
[    0.648310] PM: Writing back config space on device 0000:00:1c.0 at offset 3 (was 810000, writing 810010)
[    0.648321] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100000, writing 100407)
[    0.648382] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.648396] PM: Writing back config space on device 0000:00:1c.1 at offset f (was 40200, writing 4020b)
[    0.648409] PM: Writing back config space on device 0000:00:1c.1 at offset 9 (was 10001, writing f031f021)
[    0.648414] PM: Writing back config space on device 0000:00:1c.1 at offset 8 (was 0, writing f070f070)
[    0.648419] PM: Writing back config space on device 0000:00:1c.1 at offset 7 (was 20000000, writing 3030)
[    0.648430] PM: Writing back config space on device 0000:00:1c.1 at offset 3 (was 810000, writing 810010)
[    0.648437] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100000, writing 100407)
[    0.648479] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.648491] PM: Writing back config space on device 0000:00:1c.2 at offset f (was 40300, writing 4030a)
[    0.648509] PM: Writing back config space on device 0000:00:1c.2 at offset 6 (was 0, writing 60500)
[    0.648517] PM: Writing back config space on device 0000:00:1c.2 at offset 3 (was 810000, writing 810010)
[    0.648524] PM: Writing back config space on device 0000:00:1c.2 at offset 1 (was 100007, writing 100407)
[    0.648567] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.648576] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    0.648581] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    0.648637] usb usb1: root hub lost power or was reset
[    0.648657] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    0.648662] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    0.648715] usb usb2: root hub lost power or was reset
[    0.648735] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.648740] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    0.648793] usb usb3: root hub lost power or was reset
[    0.648817] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    0.648825] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    0.648893] usb usb4: root hub lost power or was reset
[    0.655189] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    0.655200] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    0.655304] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 10001, writing 1fff1)
[    0.655317] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was 0, writing f090f090)
[    0.655329] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 22800000, writing 228000f0)
[    0.655338] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 38070700, writing 380b0700)
[    0.655356] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100007)
[    0.655388] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.655576] PM: Writing back config space on device 0000:00:1f.2 at offset f (was 200, writing 2ff)
[    0.655613] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00005, writing 2b80005)
[    0.655641] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    0.655651] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    0.655753] PM: Writing back config space on device 0000:02:00.0 at offset f (was 100, writing 10b)
[    0.655793] PM: Writing back config space on device 0000:02:00.0 at offset 6 (was 1, writing 2001)
[    0.655810] PM: Writing back config space on device 0000:02:00.0 at offset 4 (was 4, writing f0600004)
[    0.655831] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 10)
[    0.655843] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 100000, writing 100003)
[    0.655928] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10b)
[    0.655998] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 0, writing f0700000)
[    0.656015] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 10)
[    0.656034] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100002)
[    0.656117] PM: Writing back config space on device 0000:07:06.0 at offset f (was 34001ff, writing 5c001ff)
[    0.656123] PM: Writing back config space on device 0000:07:06.0 at offset e (was 0, writing 1cfc)
[    0.656132] PM: Writing back config space on device 0000:07:06.0 at offset d (was 0, writing 1c00)
[    0.656138] PM: Writing back config space on device 0000:07:06.0 at offset c (was 0, writing 14fc)
[    0.656144] PM: Writing back config space on device 0000:07:06.0 at offset b (was 0, writing 1400)
[    0.656150] PM: Writing back config space on device 0000:07:06.0 at offset a (was 0, writing 57fff000)
[    0.656156] PM: Writing back config space on device 0000:07:06.0 at offset 9 (was 0, writing 54000000)
[    0.656163] PM: Writing back config space on device 0000:07:06.0 at offset 8 (was 0, writing 53fff000)
[    0.656169] PM: Writing back config space on device 0000:07:06.0 at offset 7 (was 0, writing 50000000)
[    0.656176] PM: Writing back config space on device 0000:07:06.0 at offset 6 (was 0, writing b00b0807)
[    0.656185] PM: Writing back config space on device 0000:07:06.0 at offset 4 (was 0, writing f0906000)
[    0.656194] PM: Writing back config space on device 0000:07:06.0 at offset 3 (was 824000, writing 82a820)
[    0.656204] PM: Writing back config space on device 0000:07:06.0 at offset 1 (was 2100000, writing 2100007)
[    0.657748] PM: Writing back config space on device 0000:07:06.1 at offset f (was 4020200, writing 402020b)
[    0.657780] PM: Writing back config space on device 0000:07:06.1 at offset 5 (was 0, writing f0900000)
[    0.707417] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0905000-f09057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    0.753806] PM: Writing back config space on device 0000:07:06.2 at offset f (was 40701ff, writing 407010a)
[    0.753837] PM: Writing back config space on device 0000:07:06.2 at offset 4 (was 0, writing f0904000)
[    0.753847] PM: Writing back config space on device 0000:07:06.2 at offset 1 (was 2100000, writing 2100006)
[    0.753872] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[    0.754348] PM: Writing back config space on device 0000:07:06.3 at offset f (was 40701ff, writing 407010a)
[    0.754382] PM: Writing back config space on device 0000:07:06.3 at offset 4 (was 0, writing f0905800)
[    0.754397] PM: Writing back config space on device 0000:07:06.3 at offset 1 (was 2100000, writing 2100006)
[    0.754426] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[    0.754477] i8042 aux 00:09: activation failed
[    0.808616] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    0.808619] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[    0.817243] ata2.00: configured for UDMA/33
[    0.867148] sd 0:0:0:0: [sda] Starting disk
[    0.930504] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    0.930506] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    0.932442] ata1.00: configured for UDMA/100
[    0.933413] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    0.933447] sd 0:0:0:0: [sda] Write Protect is off
[    0.933452] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.933531] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.934244] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[    0.935735] PM: Finishing wakeup.
[    0.935737] Restarting tasks ... <6>usb 3-2: USB disconnect, address 4
[    0.963189] done.
[    1.069103] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[    1.069109] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[    1.069211] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[    1.069235] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    1.069255] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[    1.147871] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[    1.147919] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    1.147969] sky2 0000:02:00.0: v1.20 addr 0xf0600000 irq 17 Yukon-FE (0xb7) rev 3
[    1.148751] sky2 eth0: addr 00:a0:d1:78:c5:b2
[    1.165259] sky2 eth0: enabling interface
[    1.169762] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    1.183920] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    1.188971] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[    1.212928] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    1.240656] usb 5-8: USB disconnect, address 7
[    1.246060] sky2 eth0: disabling interface
[    1.272042] sky2 eth0: enabling interface
[    1.276467] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    1.297492] usb 5-8: new high speed USB device using ehci_hcd and address 9
[    1.443765] usb 5-8: configuration #1 chosen from 1 choice
[    1.444175] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[    1.685209] usb 3-2: new full speed USB device using uhci_hcd and address 5
[    1.857590] usb 3-2: configuration #1 chosen from 1 choice
[    2.938664] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[    2.943019] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    6.098548] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.816115] eth0: no IPv6 routers present
```




1)How do I know if I less /var/log/syslog as root?
2)I am trying to suspend to mem(standby)
3)I tried:
```

sudo -i
echo -n "mem" > /sys/power/state
```

and when my laptop came out of standby my screen turned brown with color lines across it and I had to reboot. This doesn't happens when I suspend it normally.


*note: I have the spanish version of ubuntu maybe this has something to do with the error

---

### Post by ajmorris on 2008-06-13
do know if you less /var/log/syslog as root, you do 'sudo less /var/log/syslog'
Also.. did you do that straight after you came back into ubuntu after it failed?

As for the brown lines... that is a concern, the command i gave you suspends linux directly through acpi, instead of having to use some application to do it. The fact that you use spanish version will make no difference.

Well... it could be something to do with your hardware, i will have to do some googling to see if i can find any known issues with your hardware, and standby.

AJ

---

### Post by N4zgu1 on 2008-06-13
Here is the output of 

sudo less /var/log/syslog



```
Jun 12 09:49:52 carlos-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 12 09:49:52 carlos-laptop anacron[7031]: Job `cron.daily' terminated
Jun 12 09:52:28 carlos-laptop anacron[7031]: Job `cron.weekly' started
Jun 12 09:52:28 carlos-laptop anacron[8108]: Updated timestamp for job `cron.weekly' to 2008-06-12
Jun 12 09:52:30 carlos-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 12 09:52:30 carlos-laptop anacron[7031]: Job `cron.weekly' terminated
Jun 12 09:52:30 carlos-laptop anacron[7031]: Normal exit (2 jobs run)
Jun 12 09:56:34 carlos-laptop init: tty4 main process (4590) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty5 main process (4591) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty2 main process (4593) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty6 main process (4597) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty1 main process (5617) killed by TERM signal
Jun 12 09:56:34 carlos-laptop init: tty3 main process (4596) killed by TERM signal
Jun 12 09:56:34 carlos-laptop gdm[5445]: WARNING: servicio principal: Se obtuvo SIGABRT. Algo ha ido muy mal. ¡Nos caemos! 
Jun 12 09:56:34 carlos-laptop gdm[5445]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 12 09:56:34 carlos-laptop gdm[5445]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Jun 12 09:56:34 carlos-laptop avahi-daemon[5043]: Got SIGTERM, quitting.
Jun 12 09:56:34 carlos-laptop avahi-daemon[5043]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.101.79.86.
Jun 12 09:56:35 carlos-laptop kernel: [ 2050.926177] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun 12 09:56:36 carlos-laptop exiting on signal 15
Jun 12 12:51:56 carlos-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 12 12:51:56 carlos-laptop kernel: Inspecting /boot/System.map-2.6.24-18-generic
Jun 12 12:51:56 carlos-laptop kernel: Loaded 27880 symbols from /boot/System.map-2.6.24-18-generic.
Jun 12 12:51:56 carlos-laptop kernel: Symbols match kernel version 2.6.24.
Jun 12 12:51:57 carlos-laptop kernel: Loaded 19415 symbols from 97 modules.
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f670000 (usable)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 000000003f670000 - 000000003f700000 (ACPI NVS)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Jun 12 12:51:57 carlos-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
:
```





My hardware is:


*Toshiba Satellite A205
*110 gb of hard drive (35gb Vista and 75gb Ubuntu) 
*Intel core 2 duo
*2gb of ram 
I am not sure about my Graphic card but I think that it is:
*Mobile Intel(R) 945 Express Chipset Family



I dont think that it is related with my hardware because at the beginning I could suspend my laptop with no problems 


I thought that It had something to do with video codecs because I had a lot of problems installing them.
I tried to uninstall them but the problem continued I also uninstalled Wine (it was one of the first programs I installed when I got ubuntu) but the suspension problem continued and now I have no idea what is the problem that causes the suspension error

---

### Post by ajmorris on 2008-06-14
strange... i have flagged this thread for help in the Unanswered Posts team, hopefully we can find you help soon....  
Have you updated any graphics drivers or anything lately?

By the way, you posted your hardware... the command 'sudo lspci' already told me your hardware ;)  A very handy command that :)

AJ

---

