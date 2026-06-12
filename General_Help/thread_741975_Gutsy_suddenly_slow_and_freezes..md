---
title: "Gutsy suddenly slow and freezes."
date: 2008-04-01
forum: General Help
---

### Post by jfbilodeau on 2008-04-01
Good day all,

I'm hoping you can help me with a strange problem I'm having recently. My machine has plenty of CPU, RAM and diskspace, but it's suddenly very slow. It seems to work fine most of the time, but applications will freeze for a couple of second. I think this happens mostly when they access the harddisk.

Once again, my RAM is not even half-way full, my CPU is idling and the disk is not thrashing.

```
jfbilodeau@golbez:~$ df
Sys. de fich.           1K-blocs       Occupé Disponible Capacité Monté sur
/dev/sda5             19236340   8529244   9729944  47% /
varrun                  972468       296    972172   1% /var/run
varlock                 972468         0    972468   0% /var/lock
udev                    972468        80    972388   1% /dev
devshm                  972468         0    972468   0% /dev/shm
lrm                     972468     34696    937772   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1            114271592  74206808  35421040  68% /home

```

Here are the currently running apps. If I shutdown any of the desktop applications, including Firefox, Thunderbird, VirtualBox, Terminal, etc, it doesn't seem to improve performance.

```
jfbilodeau@golbez:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   31 ?        00:00:00 kblockd/0
   32 ?        00:00:00 kblockd/1
   33 ?        00:00:00 kacpid
   34 ?        00:00:00 kacpi_notify
  191 ?        00:00:00 kseriod
  219 ?        00:00:00 pdflush
  220 ?        00:00:00 pdflush
  221 ?        00:00:00 kswapd0
  272 ?        00:00:00 aio/0
  273 ?        00:00:00 aio/1
 2248 ?        00:00:00 ksuspend_usbd
 2249 ?        00:00:00 khubd
 2268 ?        00:00:00 khpsbpkt
 2288 ?        00:00:00 ata/0
 2289 ?        00:00:00 ata/1
 2290 ?        00:00:00 ata_aux
 2435 ?        00:00:00 knodemgrd_0
 2470 ?        00:00:00 scsi_eh_0
 2471 ?        00:00:00 scsi_eh_1
 2658 ?        00:00:00 kjournald
 2876 ?        00:00:00 udevd
 3915 ?        00:00:00 kmmcd
 3924 ?        00:00:00 kpsmoused
 4262 ?        00:00:00 ntos_wq/0
 4263 ?        00:00:00 ntos_wq/1
 4264 ?        00:00:00 ndis_wq
 4265 ?        00:00:00 wrapndis_wq/0
 4266 ?        00:00:00 wrapndis_wq/1
 4428 ?        00:00:00 kcryptd/0
 4429 ?        00:00:00 kcryptd/1
 4516 ?        00:00:00 kjournald
 4650 ?        00:00:00 portmap
 4669 ?        00:00:00 rpc.statd
 4814 tty4     00:00:00 getty
 4815 tty5     00:00:00 getty
 4817 tty2     00:00:00 getty
 4818 tty3     00:00:00 getty
 4819 tty1     00:00:00 getty
 4822 tty6     00:00:00 getty
 5039 ?        00:00:00 acpid
 5071 ?        00:00:00 kondemand/0
 5072 ?        00:00:00 kondemand/1
 5155 ?        00:00:00 syslogd
 5211 ?        00:00:00 dd
 5213 ?        00:00:00 klogd
 5234 ?        00:00:01 dbus-daemon
 5250 ?        00:00:00 NetworkManager
 5264 ?        00:00:00 NetworkManagerD
 5277 ?        00:00:00 system-tools-ba
 5278 ?        00:00:00 dbus-daemon
 5298 ?        00:00:01 hald
 5299 ?        00:00:00 hald-runner
 5355 ?        00:00:00 hald-addon-keyb
 5356 ?        00:00:00 hald-addon-keyb
 5357 ?        00:00:00 hald-addon-keyb
 5358 ?        00:00:00 hald-addon-keyb
 5361 ?        00:00:00 hald-addon-cpuf
 5362 ?        00:00:00 hald-addon-acpi
 5367 ?        00:00:00 hald-addon-keyb
 5391 ?        00:00:00 hald-addon-stor
 5394 ?        00:00:00 kdm
 5434 tty7     00:02:18 Xorg
 5519 ?        00:00:00 cupsd
 5548 ?        00:00:00 kdm
 5705 ?        00:00:00 lockd
 5706 ?        00:00:00 rpciod/0
 5707 ?        00:00:00 rpciod/1
 5711 ?        00:00:00 nfsd4
 5712 ?        00:00:00 nfsd
 5713 ?        00:00:00 nfsd
 5714 ?        00:00:00 nfsd
 5715 ?        00:00:00 nfsd
 5716 ?        00:00:00 nfsd
 5717 ?        00:00:00 nfsd
 5718 ?        00:00:00 nfsd
 5719 ?        00:00:00 nfsd
 5739 ?        00:00:00 rpc.mountd
 5887 ?        00:00:00 nmbd
 5917 ?        00:00:00 smbd
 5986 ?        00:00:00 smbd
 6133 ?        00:00:00 console-kit-dae
 6234 ?        00:00:00 avahi-daemon
 6235 ?        00:00:00 avahi-daemon
 6264 ?        00:00:00 dhcdbd
 6284 ?        00:00:00 hcid
 6303 ?        00:00:00 bluetoothd-serv
 6304 ?        00:00:00 bluetoothd-serv
 6307 ?        00:00:00 krfcommd
 6361 ?        00:00:00 atd
 6375 ?        00:00:00 cron
 6502 ?        00:00:00 dhclient
 6544 ?        00:00:00 timidity
 6610 ?        00:00:00 startkde
 6665 ?        00:00:00 ssh-agent
 6668 ?        00:00:00 dbus-launch
 6669 ?        00:00:00 dbus-daemon
 6702 ?        00:00:00 start_kdeinit
 6703 ?        00:00:00 kdeinit
 6706 ?        00:00:00 dcopserver
 6708 ?        00:00:00 klauncher
 6710 ?        00:00:01 kded
 6715 ?        00:00:00 kwrapper
 6717 ?        00:00:00 ksmserver
 6718 ?        00:00:05 kwin
 6720 ?        00:00:00 knotify
 6724 ?        00:00:29 artsd
 6725 ?        00:00:18 kicker
 6727 ?        00:00:00 ksysguardd
 6729 ?        00:00:00 kaccess
 6735 ?        00:00:00 kmix
 6737 ?        00:02:45 ksysguard
 6740 ?        00:00:58 ksysguardd
 6742 ?        00:00:08 amarokapp
 6744 ?        00:00:00 konsole
 6752 pts/1    00:00:00 bash
 6763 ?        00:00:03 guidance-power-
 6768 ?        00:00:00 thunderbird
 6782 ?        00:00:00 run-mozilla.sh
 6787 ?        00:00:48 thunderbird-bin
 6804 ?        00:00:00 knetworkmanager
 6806 ?        00:00:00 kblueplugd
 6808 ?        00:00:00 klipper
 6810 ?        00:00:00 python
 6811 ?        00:00:04 adept_notifier
 6816 ?        00:00:00 gconfd-2
 6846 ?        00:00:00 ruby
 6848 ?        00:00:00 kio_file
 6909 pts/1    00:00:01 VirtualBox
 6914 pts/1    00:00:00 VBoxXPCOMIPCD
 6921 ?        00:00:01 VBoxSVC
 6932 ?        00:03:45 VirtualBox
 7009 ?        00:02:28 firefox-3.0
 7232 ?        00:00:00 konsole
 7233 pts/0    00:00:00 bash
 7255 pts/0    00:00:00 ps

```

```

jfbilodeau@golbez:~$ free
             total       used       free     shared    buffers     cached
Mem:       1944940    1686136     258804          0      34876     756808
-/+ buffers/cache:     894452    1050488
Swap:            0          0          0

```

Any ideas?

EDIT: I get the same behaviour in KDE 3, Gnome, Fxce & even a terminal (CTRL+ALT+Fx).

Thanks in advance!

J-F

---

### Post by cmnorton on 2008-04-01
How much RAM do you have?

What are the speed and type of CPU?

What do the outputs of dmesg, /var/log/message and /var/log/syslog say?

---

### Post by jfbilodeau on 2008-04-02
> **cmnorton said:**
> How much RAM do you have?

What are the speed and type of CPU?

What do the outputs of dmesg, /var/log/message and /var/log/syslog say?

Here ya go:
2G RAM

AMD Turion64x2 (1.7Ghz)

dmesg:
```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077f00000 (usable)
[    0.000000]  BIOS-e820: 0000000077f00000 - 0000000077f16000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077f16000 - 0000000077f80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077f80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1023MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8910
[    0.000000] Entering add_active_range(0, 0, 491264) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   491264
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   491264
[    0.000000] On node 0 totalpages: 491264
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2046 pages used for memmap
[    0.000000]   HighMem zone: 259842 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F88E0 checksum 0
[    0.000000] ACPI: RSDP 000F88E0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 77F0CB26, 0040 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 77F15B16, 0074 (r1 HP     MCP51M    6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 77F0CB66, 8FB0 (r1 HP       MCP51M  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 77F16FC0, 0040
[    0.000000] ACPI: SSDT 77F15B8A, 0206 (r1 HP     POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 77F15D90, 003C (r1 HP       MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 77F15DCC, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 77F15E04, 005E (r1 HP     	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 77F15E62, 0028 (r1     HP $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 77F15E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 487426
[    0.000000] Kernel command line: root=UUID=ed2323b1-906d-4b2c-8bf1-b1a36221fc9b ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1908.670 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 1936280k/1965056k available (2015k kernel code, 27472k reserved, 915k data, 364k init, 1047552k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.000000] hpet0: 3 32-bit timers, 25000000 Hz
[    0.080000] Calibrating delay using timer specific routine.. 3820.62 BogoMIPS (lpj=7641255)
[    0.080000] Security Framework v1.0.0 initialized
[    0.080000] SELinux:  Disabled at boot.
[    0.080000] Mount-cache hash table entries: 512
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.080000] Compat vDSO mapped to ffffe000.
[    0.080000] Checking 'hlt' instruction... OK.
[    0.096000] SMP alternatives: switching to UP code
[    0.096000] Early unpacking initramfs... done
[    0.408000] ACPI: Core revision 20070126
[    0.408000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.416000] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[    0.416000] SMP alternatives: switching to SMP code
[    0.416000] Booting processor 1/1 eip 3000
[    0.424000] Initializing CPU#1
[    0.508000] Calibrating delay using timer specific routine.. 3817.41 BogoMIPS (lpj=7634827)
[    0.508000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.508000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.508000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.508000] CPU 1(2) -> Core 1
[    0.508000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.508000] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[    0.508000] Total of 2 processors activated (7638.04 BogoMIPS).
[    0.508000] ENABLING IO-APIC IRQs
[    0.508000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.552000] Brought up 2 CPUs
[    0.608000] migration_cost=4000
[    0.608000] Booting paravirtualized kernel on bare hardware
[    0.608000] Time: 23:51:24  Date: 03/01/108
[    0.608000] NET: Registered protocol family 16
[    0.608000] EISA bus registered
[    0.608000] ACPI: bus type pci registered
[    0.624000] PCI: BIOS BUG #81[49435000] found
[    0.624000] PCI: Using configuration type 1
[    0.624000] Setting up standard PCI resources
[    0.624000] ACPI: EC: Look up EC in DSDT
[    0.624000] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[    0.628000] ACPI: System BIOS is requesting _OSI(Linux)
[    0.628000] ACPI: Please test with "acpi_osi=!Linux"
[    0.628000] Please send dmidecode to linux-acpi@vger.kernel.org
[    0.628000] ACPI: Interpreter enabled
[    0.628000] ACPI: (supports S0 S3 S4 S5)
[    0.628000] ACPI: Using IOAPIC for interrupt routing
[    0.632000] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[    0.632000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.632000] PCI: Probing PCI hardware (bus 00)
[    0.636000] PCI: Transparent bridge - 0000:00:10.0
[    0.636000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.636000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.636000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.636000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.668000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.668000] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[    0.668000] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *11
[    0.668000] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.668000] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[    0.668000] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[    0.668000] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.668000] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.668000] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[    0.672000] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[    0.672000] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.672000] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[    0.672000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.672000] pnp: PnP ACPI init
[    0.672000] ACPI: bus type pnp registered
[    0.672000] pnp: PnP ACPI: found 13 devices
[    0.672000] ACPI: ACPI bus type pnp unregistered
[    0.672000] PnPBIOS: Disabled by ACPI PNP
[    0.672000] PCI: Using ACPI for IRQ routing
[    0.672000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.672000] NET: Registered protocol family 8
[    0.672000] NET: Registered protocol family 20
[    0.672000] pnp: 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.672000] pnp: 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.672000] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.672000] pnp: 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.672000] pnp: 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.672000] pnp: 00:03: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.672000] pnp: 00:04: ioport range 0x1000-0x107f has been reserved
[    0.672000] pnp: 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.672000] pnp: 00:04: ioport range 0x1400-0x147f has been reserved
[    0.672000] pnp: 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.672000] pnp: 00:04: ioport range 0x1800-0x187f has been reserved
[    0.672000] pnp: 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.672000] pnp: 00:04: ioport range 0x2000-0x203f has been reserved
[    0.676000] Time: hpet clocksource has been installed.
[    0.704000] PCI: Bridge: 0000:00:02.0
[    0.704000]   IO window: 4000-4fff
[    0.704000]   MEM window: b4000000-b5ffffff
[    0.704000]   PREFETCH window: d0000000-d01fffff
[    0.704000] PCI: Bridge: 0000:00:03.0
[    0.704000]   IO window: disabled.
[    0.704000]   MEM window: b6000000-b7ffffff
[    0.704000]   PREFETCH window: disabled.
[    0.704000] PCI: Bridge: 0000:00:10.0
[    0.704000]   IO window: disabled.
[    0.704000]   MEM window: b8000000-b80fffff
[    0.704000]   PREFETCH window: disabled.
[    0.704000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.704000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.704000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    0.704000] NET: Registered protocol family 2
[    0.760000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.760000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.760000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.760000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.760000] TCP reno registered
[    0.776000] checking if image is initramfs... it is
[    1.392000] Freeing initrd memory: 7387k freed
[    1.392000] Simple Boot Flag at 0x36 set to 0x1
[    1.392000] audit: initializing netlink socket (disabled)
[    1.392000] audit(1207093884.176:1): initialized
[    1.392000] highmem bounce pool size: 64 pages
[    1.396000] VFS: Disk quotas dquot_6.5.1
[    1.396000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.396000] io scheduler noop registered
[    1.396000] io scheduler anticipatory registered
[    1.396000] io scheduler deadline registered
[    1.396000] io scheduler cfq registered (default)
[    1.396000] Boot video device is 0000:00:05.0
[    1.416000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.416000] assign_interrupt_mode Found MSI capability
[    1.416000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.416000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.416000] assign_interrupt_mode Found MSI capability
[    1.416000] Allocate Port Service[0000:00:03.0:pcie00]
[    1.416000] isapnp: Scanning for PnP cards...
[    1.768000] isapnp: No Plug & Play device found
[    1.788000] Real Time Clock Driver v1.12ac
[    1.788000] hpet_resources: 0xfed00000 is busy
[    1.788000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.792000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.792000] input: Macintosh mouse button emulation as /class/input/input0
[    1.792000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.808000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.808000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.808000] mice: PS/2 mouse device common for all mice
[    1.808000] EISA: Probing bus 0 at eisa.0
[    1.808000] Cannot allocate resource for EISA slot 1
[    1.808000] Cannot allocate resource for EISA slot 2
[    1.808000] Cannot allocate resource for EISA slot 3
[    1.808000] Cannot allocate resource for EISA slot 4
[    1.808000] EISA: Detected 0 cards.
[    1.808000] TCP cubic registered
[    1.808000] NET: Registered protocol family 1
[    1.808000] Using IPI No-Shortcut mode
[    1.808000]   Magic number: 4:840:907
[    1.808000]   hash matches device ptyz3
[    1.812000] Freeing unused kernel memory: 364k freed
[    1.824000] input: AT Translated Set 2 keyboard as /class/input/input1
[    3.036000] AppArmor: AppArmor initialized<5>audit(1207093886.176:2):  type=1505 info="AppArmor initialized" pid=1269
[    3.044000] fuse init (API version 7.8)
[    3.052000] Failure registering capabilities with primary security module.
[    3.092000] ACPI: Thermal Zone [THRM] (29 C)
[    3.704000] usbcore: registered new interface driver usbfs
[    3.704000] usbcore: registered new interface driver hub
[    3.704000] usbcore: registered new device driver usb
[    3.704000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    3.704000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 16
[    3.704000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    3.704000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    3.704000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    3.704000] ehci_hcd 0000:00:0b.1: debug port 1
[    3.704000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[    3.704000] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xb0005000
[    3.704000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.704000] usb usb1: configuration #1 chosen from 1 choice
[    3.704000] hub 1-0:1.0: USB hub found
[    3.704000] hub 1-0:1.0: 8 ports detected
[    3.716000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.716000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.736000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    3.820000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    3.820000] NFORCE-MCP51: chipset revision 241
[    3.820000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    3.820000] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[    3.820000] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[    3.820000]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[    3.820000] Probing IDE interface ide0...
[    3.836000] SCSI subsystem initialized
[    3.844000] libata version 2.21 loaded.
[    3.852000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.068000] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    4.216000] usb 1-4: configuration #1 chosen from 1 choice
[    4.576000] hda: HL-DT-ST DVDRAM GSA-T20L, ATAPI CD/DVD-ROM drive
[    4.924000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.928000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.928000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 20 (level, high) -> IRQ 17
[    4.928000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    4.928000] forcedeth: using HIGHDMA
[    4.936000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[    4.936000] Uniform CD-ROM driver Revision: 3.20
[    5.448000] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[    5.448000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    5.448000] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 5 (level, high) -> IRQ 5
[    5.452000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    5.452000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 22 (level, high) -> IRQ 16
[    5.452000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    5.452000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    5.452000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    5.452000] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xb0004000
[    5.500000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.508000] usb usb2: configuration #1 chosen from 1 choice
[    5.508000] hub 2-0:1.0: USB hub found
[    5.508000] hub 2-0:1.0: 8 ports detected
[    5.612000] sata_nv 0000:00:0e.0: version 3.4
[    5.612000] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[    5.612000] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    5.612000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 23 (level, high) -> IRQ 18
[    5.612000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    5.612000] scsi0 : sata_nv
[    5.612000] scsi1 : sata_nv
[    5.612000] ata1: SATA max UDMA/133 cmd 0x000130c0 ctl 0x000130b6 bmdma 0x00013090 irq 18
[    5.612000] ata2: SATA max UDMA/133 cmd 0x000130b8 ctl 0x000130b2 bmdma 0x00013098 irq 18
[    6.080000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.088000] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC7BP, max UDMA/100
[    6.088000] ata1.00: 312581808 sectors, multi 16: LBA48 
[    6.104000] ata1.00: configured for UDMA/100
[    6.420000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.424000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[    6.432000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.432000] sd 0:0:0:0: [sda] Write Protect is off
[    6.432000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.432000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.432000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.432000] sd 0:0:0:0: [sda] Write Protect is off
[    6.432000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.432000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.432000]  sda: sda1 sda2 sda4 < sda5 sda6 >
[    6.512000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.516000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.784000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0068024000]
[    6.840000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.840000] EXT3-fs: write access will be enabled during recovery.
[    8.088000] usb 2-6: new low speed USB device using ohci_hcd and address 2
[    8.300000] usb 2-6: configuration #1 chosen from 1 choice
[    8.312000] usbcore: registered new interface driver hiddev
[    8.320000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[    8.320000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-6
[    8.320000] usbcore: registered new interface driver usbhid
[    8.320000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   10.408000] kjournald starting.  Commit interval 5 seconds
[   10.408000] EXT3-fs: sda5: orphan cleanup on readonly fs
[   10.408000] ext3_orphan_cleanup: deleting unreferenced inode 961378
[   10.408000] EXT3-fs: sda5: 1 orphan inode deleted
[   10.408000] EXT3-fs: recovery complete.
[   10.408000] EXT3-fs: mounted filesystem with ordered data mode.
[   27.280000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.324000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.684000] Linux agpgart interface v0.102 (c) Dave Jones
[   27.836000] input: PC Speaker as /class/input/input3
[   27.872000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   27.872000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   27.912000] nvidia: module license 'NVIDIA' taints kernel.
[   28.192000] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   28.192000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 18 (level, high) -> IRQ 19
[   28.192000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   28.192000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   28.192000] sdhci: Secure Digital Host Controller Interface driver
[   28.192000] sdhci: Copyright(c) Pierre Ossman
[   28.192000] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   28.192000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   28.192000] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 7 (level, high) -> IRQ 7
[   28.192000] mmc0: SDHCI at 0xb8000800 irq 7 DMA
[   28.476000] Linux video capture interface: v2.00
[   28.680000] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   28.680000] usbcore: registered new interface driver uvcvideo
[   28.680000] USB Video Class driver (v0.1.0)
[   28.916000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   28.916000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 21 (level, high) -> IRQ 20
[   28.916000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   29.000000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   29.068000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   29.512000] lp: driver loaded but no devices found
[   29.600000] ndiswrapper version 1.45 loaded (smp=yes)
[   29.680000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   29.680000] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   29.680000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, high) -> IRQ 21
[   29.680000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   29.688000] ndiswrapper: using IRQ 21
[   30.040000] wlan0: ethernet device 00:1a:73:7f:13:f1 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[   30.040000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   30.044000] usbcore: registered new interface driver ndiswrapper
[   30.724000] EXT3 FS on sda5, internal journal
[   31.008000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   37.204000] kjournald starting.  Commit interval 5 seconds
[   37.204000] EXT3 FS on sda1, internal journal
[   37.204000] EXT3-fs: mounted filesystem with ordered data mode.
[   41.816000] input: Power Button (FF) as /class/input/input5
[   41.816000] ACPI: Power Button (FF) [PWRF]
[   41.820000] input: Power Button (CM) as /class/input/input6
[   41.820000] ACPI: Power Button (CM) [PWRB]
[   41.848000] input: Sleep Button (CM) as /class/input/input7
[   41.848000] ACPI: Sleep Button (CM) [SLPB]
[   41.864000] input: Lid Switch as /class/input/input8
[   41.864000] ACPI: Lid Switch [LID]
[   41.936000] No dock devices found.
[   42.048000] ACPI: Battery Slot [BAT0] (battery present)
[   42.088000] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   42.088000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   42.116000] ACPI: AC Adapter [ACAD] (on-line)
[   42.448000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (version 2.00.00)
[   42.448000] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x13
[   42.448000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[   42.448000] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[   42.448000] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   43.872000] eth0: no link during initialization.
[   44.188000] ppdev: user-space parallel port driver
[   45.056000] audit(1207093928.733:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5454 profile="/usr/sbin/cupsd"
[   46.260000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   46.544000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   46.564000] NFSD: starting 90-second grace period
[   48.000000] Clocksource tsc unstable (delta = -289494076 ns)
[   52.792000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   52.792000] vboxdrv: Successfully done.
[   53.260000] Failure registering capabilities with primary security module.
[   53.568000] Bluetooth: Core ver 2.11
[   53.568000] NET: Registered protocol family 31
[   53.568000] Bluetooth: HCI device and connection manager initialized
[   53.568000] Bluetooth: HCI socket layer initialized
[   53.572000] Bluetooth: L2CAP ver 2.8
[   53.572000] Bluetooth: L2CAP socket layer initialized
[   53.660000] Bluetooth: RFCOMM socket layer initialized
[   53.660000] Bluetooth: RFCOMM TTY layer initialized
[   53.660000] Bluetooth: RFCOMM ver 1.8
[  122.044000] NET: Registered protocol family 10
[  122.048000] lo: Disabled Privacy Extensions
[  122.048000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  122.048000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  140.248000] NET: Registered protocol family 17
[  170.000000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  184.516000] wlan0: no IPv6 routers present
[47773.248000] usb 2-6: USB disconnect, address 2
[47985.044000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[47998.052000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48004.172000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[48007.368000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48020.376000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48033.388000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48046.392000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48059.396000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48072.404000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48085.412000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48098.420000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48111.428000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48124.436000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48137.444000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48150.448000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48163.452000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48176.460000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48189.468000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48202.476000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48215.484000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48228.492000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48241.504000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48254.516000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48267.524000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48280.536000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48293.548000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48306.568000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48319.580000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48332.596000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48345.612000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48358.620000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48371.632000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48384.636000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48397.640000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48410.644000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48423.652000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48436.660000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48449.672000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48462.680000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48475.688000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48488.696000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48501.704000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48514.712000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48527.716000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48540.724000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48553.728000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48566.732000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48579.736000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48592.740000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48605.744000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48618.748000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48631.752000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48644.756000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48657.760000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48670.764000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48683.768000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48696.772000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48709.776000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48722.780000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48735.784000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48748.788000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48761.792000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48774.796000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48787.800000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48800.804000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48813.808000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48826.812000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48839.816000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48852.820000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48865.824000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48878.828000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48891.832000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48904.836000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48917.840000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48930.844000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48943.848000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48956.852000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48969.860000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48982.864000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[48995.868000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49008.872000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49021.876000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49034.880000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49047.884000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49060.888000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49073.892000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49086.900000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49099.912000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49112.916000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49125.932000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49138.936000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49151.940000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49164.948000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49173.516000] usb 2-6: new low speed USB device using ohci_hcd and address 3
[49173.716000] usb 2-6: configuration #1 chosen from 1 choice
[49173.728000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input9
[49173.728000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-6
[49177.952000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49190.960000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49203.976000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49216.984000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49229.992000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49243.004000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49256.012000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49269.032000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49280.956000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[49315.160000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[49315.692000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[49334.088000] wlan0: no IPv6 routers present
[49429.980000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[49434.916000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[49452.708000] wlan0: no IPv6 routers present
[49629.588000] eth0: link up.
[49629.592000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[49640.588000] eth0: no IPv6 routers present
[50807.660000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50811.344000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[50825.792000] wlan0: no IPv6 routers present

```

/var/log/message
```

Apr  2 07:50:37 golbez syslogd 1.4.1#21ubuntu3: restart.
Apr  2 08:12:09 golbez -- MARK --
Apr  2 08:32:09 golbez -- MARK --
Apr  2 08:52:09 golbez -- MARK --
Apr  2 09:07:40 golbez kernel: [47773.248000] usb 2-6: USB disconnect, address 2
Apr  2 09:11:11 golbez kernel: [47985.044000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:11:24 golbez kernel: [47998.052000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:11:31 golbez kernel: [48004.172000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  2 09:11:34 golbez kernel: [48007.368000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:11:47 golbez kernel: [48020.376000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:00 golbez kernel: [48033.388000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:13 golbez kernel: [48046.392000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:26 golbez kernel: [48059.396000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:39 golbez kernel: [48072.404000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:52 golbez kernel: [48085.412000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:05 golbez kernel: [48098.420000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:18 golbez kernel: [48111.428000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:31 golbez kernel: [48124.436000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:44 golbez kernel: [48137.444000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:57 golbez kernel: [48150.448000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:14:10 golbez kernel: [48163.452000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:14:23 golbez kernel: [48176.460000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:14:36 golbez kernel: [48189.468000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:14:49 golbez kernel: [48202.476000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:02 golbez kernel: [48215.484000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:15 golbez kernel: [48228.492000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:28 golbez kernel: [48241.504000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:41 golbez kernel: [48254.516000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:54 golbez kernel: [48267.524000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:07 golbez kernel: [48280.536000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:20 golbez kernel: [48293.548000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:33 golbez kernel: [48306.568000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:46 golbez kernel: [48319.580000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:59 golbez kernel: [48332.596000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:17:12 golbez kernel: [48345.612000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:17:25 golbez kernel: [48358.620000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:17:38 golbez kernel: [48371.632000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:17:51 golbez kernel: [48384.636000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:04 golbez kernel: [48397.640000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:17 golbez kernel: [48410.644000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:30 golbez kernel: [48423.652000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:43 golbez kernel: [48436.660000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:56 golbez kernel: [48449.672000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:19:09 golbez kernel: [48462.680000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:19:22 golbez kernel: [48475.688000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:19:35 golbez kernel: [48488.696000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:19:48 golbez kernel: [48501.704000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:01 golbez kernel: [48514.712000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:14 golbez kernel: [48527.716000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:27 golbez kernel: [48540.724000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:40 golbez kernel: [48553.728000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:53 golbez kernel: [48566.732000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:06 golbez kernel: [48579.736000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:19 golbez kernel: [48592.740000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:32 golbez kernel: [48605.744000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:45 golbez kernel: [48618.748000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:58 golbez kernel: [48631.752000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:22:11 golbez kernel: [48644.756000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:22:24 golbez kernel: [48657.760000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:22:37 golbez kernel: [48670.764000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:22:50 golbez kernel: [48683.768000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:03 golbez kernel: [48696.772000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:16 golbez kernel: [48709.776000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:29 golbez kernel: [48722.780000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:42 golbez kernel: [48735.784000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:55 golbez kernel: [48748.788000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:24:08 golbez kernel: [48761.792000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:24:21 golbez kernel: [48774.796000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:24:34 golbez kernel: [48787.800000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:24:47 golbez kernel: [48800.804000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:00 golbez kernel: [48813.808000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:13 golbez kernel: [48826.812000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:26 golbez kernel: [48839.816000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:39 golbez kernel: [48852.820000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:52 golbez kernel: [48865.824000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:05 golbez kernel: [48878.828000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:18 golbez kernel: [48891.832000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:31 golbez kernel: [48904.836000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:44 golbez kernel: [48917.840000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:57 golbez kernel: [48930.844000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:27:10 golbez kernel: [48943.848000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:27:23 golbez kernel: [48956.852000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:27:36 golbez kernel: [48969.860000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:27:49 golbez kernel: [48982.864000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:02 golbez kernel: [48995.868000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:15 golbez kernel: [49008.872000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:28 golbez kernel: [49021.876000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:41 golbez kernel: [49034.880000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:54 golbez kernel: [49047.884000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:07 golbez kernel: [49060.888000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:20 golbez kernel: [49073.892000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:33 golbez kernel: [49086.900000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:46 golbez kernel: [49099.912000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:59 golbez kernel: [49112.916000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:30:12 golbez kernel: [49125.932000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:30:25 golbez kernel: [49138.936000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:30:38 golbez kernel: [49151.940000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:30:51 golbez kernel: [49164.948000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:00 golbez kernel: [49173.516000] usb 2-6: new low speed USB device using ohci_hcd and address 3
Apr  2 09:31:00 golbez kernel: [49173.716000] usb 2-6: configuration #1 chosen from 1 choice
Apr  2 09:31:00 golbez kernel: [49173.728000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input9
Apr  2 09:31:00 golbez kernel: [49173.728000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-6
Apr  2 09:31:04 golbez kernel: [49177.952000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:17 golbez kernel: [49190.960000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:30 golbez kernel: [49203.976000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:43 golbez kernel: [49216.984000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:56 golbez kernel: [49229.992000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:32:09 golbez kernel: [49243.004000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:32:22 golbez kernel: [49256.012000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:32:35 golbez kernel: [49269.032000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:32:47 golbez kernel: [49280.956000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  2 09:33:22 golbez kernel: [49315.160000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:33:22 golbez kernel: [49315.692000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  2 09:33:29 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Apr  2 09:33:29 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Apr  2 09:33:29 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Apr  2 09:35:16 golbez kernel: [49429.980000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  2 09:35:21 golbez kernel: [49434.916000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  2 09:35:28 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Apr  2 09:35:28 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Apr  2 09:35:28 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Apr  2 09:38:36 golbez kernel: [49629.588000] eth0: link up.
Apr  2 09:38:36 golbez kernel: [49629.592000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  2 09:52:10 golbez -- MARK --
Apr  2 09:58:14 golbez kernel: [50807.660000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  2 09:58:18 golbez kernel: [50811.344000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  2 09:58:21 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Apr  2 09:58:21 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Apr  2 09:58:21 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Apr  2 09:58:21 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Apr  2 10:12:05 golbez -- MARK --

```

/var/log/syslog
```

Apr  2 07:49:15 golbez syslogd 1.4.1#21ubuntu3: restart.
Apr  2 07:49:15 golbez anacron[10432]: Job `cron.daily' terminated
Apr  2 07:49:15 golbez anacron[10432]: Job `cron.weekly' started
Apr  2 07:49:15 golbez anacron[10798]: Updated timestamp for job `cron.weekly' to 2008-04-02
Apr  2 07:50:37 golbez syslogd 1.4.1#21ubuntu3: restart.
Apr  2 07:50:37 golbez anacron[10432]: Job `cron.weekly' terminated
Apr  2 07:50:37 golbez anacron[10432]: Normal exit (2 jobs run)
Apr  2 08:09:01 golbez /USR/SBIN/CRON[11093]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  2 08:17:01 golbez /USR/SBIN/CRON[11146]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  2 08:32:09 golbez -- MARK --
Apr  2 08:39:01 golbez /USR/SBIN/CRON[11297]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  2 08:52:09 golbez -- MARK --
Apr  2 09:07:40 golbez kernel: [47773.248000] usb 2-6: USB disconnect, address 2
Apr  2 09:07:40 golbez NetworkManager: <debug> [1207141660.101790] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_40_noserial_if0_logicaldev_input'). 
Apr  2 09:07:40 golbez NetworkManager: <debug> [1207141660.102104] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_40_noserial_if0'). 
Apr  2 09:07:40 golbez NetworkManager: <debug> [1207141660.104387] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_40_noserial_usbraw'). 
Apr  2 09:07:40 golbez NetworkManager: <debug> [1207141660.107016] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_40_noserial'). 
Apr  2 09:09:01 golbez /USR/SBIN/CRON[11550]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  2 09:11:11 golbez kernel: [47985.044000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:11:24 golbez kernel: [47998.052000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:11:28 golbez NetworkManager: <info>  wlan0: link timed out. 
Apr  2 09:11:28 golbez NetworkManager: <info>  SWITCH: found better connection 'wlan0/chronogears.local' than current connection 'wlan0/chronogears.local'.  same_ssid=1, have_link=0 
Apr  2 09:11:28 golbez NetworkManager: <info>  Will activate connection 'wlan0/chronogears.local'. 
Apr  2 09:11:28 golbez NetworkManager: <info>  Device wlan0 activation scheduled... 
Apr  2 09:11:28 golbez NetworkManager: <info>  Deactivating device wlan0. 
Apr  2 09:11:28 golbez dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 6340
Apr  2 09:11:28 golbez dhclient: killed old client process, removed PID file
Apr  2 09:11:28 golbez dhclient: DHCPRELEASE on wlan0 to 192.169.0.1 port 67
Apr  2 09:11:28 golbez avahi-daemon[5766]: Withdrawing address record for 192.169.0.122 on wlan0.
Apr  2 09:11:28 golbez avahi-daemon[5766]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.169.0.122.
Apr  2 09:11:28 golbez avahi-daemon[5766]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  2 09:11:29 golbez avahi-daemon[5766]: Withdrawing address record for fe80::21a:73ff:fe7f:13f1 on wlan0.
Apr  2 09:11:29 golbez NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Apr  2 09:11:29 golbez NetworkManager: <info>  Activation (wlan0) started... 
Apr  2 09:11:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  2 09:11:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr  2 09:11:29 golbez NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Apr  2 09:11:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  2 09:11:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr  2 09:11:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr  2 09:11:29 golbez NetworkManager: <info>  Activation (wlan0/wireless): access point 'chronogears.local' is encrypted, and a key exists.  No new key needed. 
Apr  2 09:11:29 golbez NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface wlan0 
Apr  2 09:11:29 golbez NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Apr  2 09:11:30 golbez NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Apr  2 09:11:30 golbez NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant5^I' 
Apr  2 09:11:31 golbez kernel: [48004.172000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:11:31 golbez NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: response was '0' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6368726f6e6f67656172732e6c6f63616c' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr  2 09:11:31 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:11:31 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 09:11:34 golbez kernel: [48007.368000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:11:47 golbez kernel: [48020.376000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:00 golbez kernel: [48033.388000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:13 golbez kernel: [48046.392000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:26 golbez kernel: [48059.396000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:31 golbez NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), asking for new key. 
Apr  2 09:12:31 golbez NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'chronogears.local'. 
Apr  2 09:12:39 golbez kernel: [48072.404000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:12:52 golbez kernel: [48085.412000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:05 golbez kernel: [48098.420000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:18 golbez kernel: [48111.428000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:31 golbez kernel: [48124.436000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:44 golbez kernel: [48137.444000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:13:57 golbez kernel: [48150.448000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:14:10 golbez kernel: [48163.452000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:14:23 golbez kernel: [48176.460000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:14:36 golbez kernel: [48189.468000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:14:49 golbez kernel: [48202.476000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:02 golbez kernel: [48215.484000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:15 golbez kernel: [48228.492000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:28 golbez kernel: [48241.504000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:41 golbez kernel: [48254.516000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:15:54 golbez kernel: [48267.524000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:07 golbez kernel: [48280.536000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:20 golbez kernel: [48293.548000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:33 golbez kernel: [48306.568000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:46 golbez kernel: [48319.580000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:16:59 golbez kernel: [48332.596000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:17:01 golbez /USR/SBIN/CRON[11625]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  2 09:17:12 golbez kernel: [48345.612000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:17:25 golbez kernel: [48358.620000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:17:38 golbez kernel: [48371.632000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:17:51 golbez kernel: [48384.636000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:04 golbez kernel: [48397.640000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:17 golbez kernel: [48410.644000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:30 golbez kernel: [48423.652000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:43 golbez kernel: [48436.660000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:18:56 golbez kernel: [48449.672000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:19:09 golbez kernel: [48462.680000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:19:22 golbez kernel: [48475.688000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:19:35 golbez kernel: [48488.696000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:19:48 golbez kernel: [48501.704000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:01 golbez kernel: [48514.712000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:14 golbez kernel: [48527.716000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:27 golbez kernel: [48540.724000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:40 golbez kernel: [48553.728000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:20:53 golbez kernel: [48566.732000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:06 golbez kernel: [48579.736000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:19 golbez kernel: [48592.740000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:32 golbez kernel: [48605.744000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:45 golbez kernel: [48618.748000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:21:58 golbez kernel: [48631.752000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:22:11 golbez kernel: [48644.756000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:22:24 golbez kernel: [48657.760000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:22:37 golbez kernel: [48670.764000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:22:50 golbez kernel: [48683.768000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:03 golbez kernel: [48696.772000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:16 golbez kernel: [48709.776000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:29 golbez kernel: [48722.780000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:42 golbez kernel: [48735.784000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:23:55 golbez kernel: [48748.788000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:24:08 golbez kernel: [48761.792000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:24:21 golbez kernel: [48774.796000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:24:34 golbez kernel: [48787.800000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:24:47 golbez kernel: [48800.804000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:00 golbez kernel: [48813.808000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:13 golbez kernel: [48826.812000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:26 golbez kernel: [48839.816000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:39 golbez kernel: [48852.820000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:25:52 golbez kernel: [48865.824000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:05 golbez kernel: [48878.828000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:18 golbez kernel: [48891.832000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:31 golbez kernel: [48904.836000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:44 golbez kernel: [48917.840000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:26:57 golbez kernel: [48930.844000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:27:10 golbez kernel: [48943.848000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:27:23 golbez kernel: [48956.852000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:27:36 golbez kernel: [48969.860000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:27:49 golbez kernel: [48982.864000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:02 golbez kernel: [48995.868000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:15 golbez kernel: [49008.872000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:28 golbez kernel: [49021.876000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:41 golbez kernel: [49034.880000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:28:54 golbez kernel: [49047.884000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:07 golbez kernel: [49060.888000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:20 golbez kernel: [49073.892000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:33 golbez kernel: [49086.900000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:46 golbez kernel: [49099.912000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:29:59 golbez kernel: [49112.916000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:30:12 golbez kernel: [49125.932000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:30:25 golbez kernel: [49138.936000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:30:31 golbez anacron[11692]: Anacron 2.3 started on 2008-04-02
Apr  2 09:30:31 golbez anacron[11692]: Normal exit (0 jobs run)
Apr  2 09:30:38 golbez kernel: [49151.940000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:30:51 golbez kernel: [49164.948000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:00 golbez kernel: [49173.516000] usb 2-6: new low speed USB device using ohci_hcd and address 3
Apr  2 09:31:00 golbez kernel: [49173.716000] usb 2-6: configuration #1 chosen from 1 choice
Apr  2 09:31:00 golbez NetworkManager: <debug> [1207143060.641890] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_40_noserial'). 
Apr  2 09:31:00 golbez kernel: [49173.728000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input9
Apr  2 09:31:00 golbez kernel: [49173.728000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-6
Apr  2 09:31:00 golbez NetworkManager: <debug> [1207143060.775019] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_40_noserial_if0'). 
Apr  2 09:31:00 golbez NetworkManager: <debug> [1207143060.833356] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_40_noserial_usbraw'). 
Apr  2 09:31:01 golbez NetworkManager: <debug> [1207143061.004542] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_40_noserial_if0_logicaldev_input'). 
Apr  2 09:31:04 golbez kernel: [49177.952000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:17 golbez kernel: [49190.960000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:30 golbez kernel: [49203.976000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:43 golbez kernel: [49216.984000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:31:56 golbez kernel: [49229.992000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:32:09 golbez kernel: [49243.004000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:32:22 golbez kernel: [49256.012000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:32:35 golbez kernel: [49269.032000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:32:40 golbez NetworkManager: <WARN>  nm_dbus_get_user_key_for_network_cb(): nm_dbus_get_user_key_for_network_cb(): dbus returned an error.   (org.freedesktop.NetworkManagerInfo.GetKeyError) org.freedesktop.NetworkManagerInfo.GetKeyError  
Apr  2 09:32:40 golbez NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Apr  2 09:32:40 golbez NetworkManager: <info>  Activation (wlan0) failed for access point (chronogears.local) 
Apr  2 09:32:40 golbez NetworkManager: <info>  Activation (wlan0) failed. 
Apr  2 09:32:40 golbez NetworkManager: <info>  Deactivating device wlan0. 
Apr  2 09:32:40 golbez NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Apr  2 09:32:47 golbez kernel: [49280.956000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  2 09:32:57 golbez NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
Apr  2 09:32:57 golbez NetworkManager: <info>  Will activate connection 'wlan0/Gatineau'. 
Apr  2 09:32:57 golbez NetworkManager: <info>  Device wlan0 activation scheduled... 
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0) started... 
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0/wireless): access point 'Gatineau' is encrypted, but NO valid key exists.  New key needed. 
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Gatineau'. 
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 09:32:57 golbez NetworkManager: <WARN>  nm_dbus_get_user_key_for_network_cb(): nm_dbus_get_user_key_for_network_cb(): dbus returned an error.   (org.freedesktop.NetworkManagerInfo.GetKeyError) org.freedesktop.NetworkManagerInfo.GetKeyError  
Apr  2 09:32:57 golbez NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) failed for access point (Gatineau) 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) failed. 
Apr  2 09:32:58 golbez NetworkManager: <info>  Deactivating device wlan0. 
Apr  2 09:32:58 golbez NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Apr  2 09:32:58 golbez NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
Apr  2 09:32:58 golbez NetworkManager: <info>  Will activate connection 'wlan0/Ottawa'. 
Apr  2 09:32:58 golbez NetworkManager: <info>  Device wlan0 activation scheduled... 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) started... 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0/wireless): access point 'Ottawa' is encrypted, but NO valid key exists.  New key needed. 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Ottawa'. 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 09:32:58 golbez NetworkManager: <WARN>  nm_dbus_get_user_key_for_network_cb(): nm_dbus_get_user_key_for_network_cb(): dbus returned an error.   (org.freedesktop.NetworkManagerInfo.GetKeyError) org.freedesktop.NetworkManagerInfo.GetKeyError  
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) failed for access point (Ottawa) 
Apr  2 09:32:58 golbez NetworkManager: <info>  Activation (wlan0) failed. 
Apr  2 09:32:58 golbez NetworkManager: <info>  Deactivating device wlan0. 
Apr  2 09:32:58 golbez NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Apr  2 09:33:17 golbez NetworkManager: <debug> [1207143197.626363] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Ottawa' 
Apr  2 09:33:17 golbez NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Ottawa 
Apr  2 09:33:17 golbez NetworkManager: <info>  Deactivating device wlan0. 
Apr  2 09:33:17 golbez NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Apr  2 09:33:17 golbez NetworkManager: <info>  Device wlan0 activation scheduled... 
Apr  2 09:33:17 golbez NetworkManager: <info>  Activation (wlan0) started... 
Apr  2 09:33:17 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  2 09:33:17 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr  2 09:33:17 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  2 09:33:17 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr  2 09:33:17 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr  2 09:33:17 golbez NetworkManager: <info>  Activation (wlan0/wireless): access point 'Ottawa' is encrypted, and a key exists.  No new key needed. 
Apr  2 09:33:18 golbez NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Apr  2 09:33:18 golbez NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Apr  2 09:33:18 golbez NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant2^I' 
Apr  2 09:33:18 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:33:18 golbez NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: response was '0' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4f7474617761' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr  2 09:33:19 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:33:19 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 09:33:22 golbez kernel: [49315.160000] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
Apr  2 09:33:22 golbez kernel: [49315.692000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  2 09:33:22 golbez NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Ottawa'. 
Apr  2 09:33:22 golbez NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  2 09:33:22 golbez NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Apr  2 09:33:23 golbez NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Apr  2 09:33:23 golbez dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Apr  2 09:33:23 golbez NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  2 09:33:23 golbez NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Apr  2 09:33:24 golbez avahi-daemon[5766]: Registering new address record for fe80::21a:73ff:fe7f:13f1 on wlan0.*.
Apr  2 09:33:24 golbez NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Apr  2 09:33:28 golbez dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr  2 09:33:29 golbez dhclient: DHCPOFFER from 192.168.4.1
Apr  2 09:33:29 golbez dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Apr  2 09:33:29 golbez dhclient: DHCPACK from 192.168.4.1
Apr  2 09:33:29 golbez avahi-daemon[5766]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.4.100.
Apr  2 09:33:29 golbez avahi-daemon[5766]: New relevant interface wlan0.IPv4 for mDNS.
Apr  2 09:33:29 golbez avahi-daemon[5766]: Registering new address record for 192.168.4.100 on wlan0.IPv4.
Apr  2 09:33:29 golbez NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Apr  2 09:33:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  2 09:33:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Apr  2 09:33:29 golbez dhclient: bound to 192.168.4.100 -- renewal in 36029 seconds.
Apr  2 09:33:29 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Apr  2 09:33:29 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Apr  2 09:33:29 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Apr  2 09:33:29 golbez NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  2 09:33:29 golbez NetworkManager: <info>    address 192.168.4.100 
Apr  2 09:33:29 golbez NetworkManager: <info>    netmask 255.255.255.0 
Apr  2 09:33:29 golbez NetworkManager: <info>    broadcast 192.168.4.255 
Apr  2 09:33:29 golbez NetworkManager: <info>    gateway 192.168.4.1 
Apr  2 09:33:29 golbez NetworkManager: <info>    nameserver 206.47.244.101 
Apr  2 09:33:29 golbez NetworkManager: <info>    nameserver 206.47.244.102 
Apr  2 09:33:29 golbez NetworkManager: <info>    hostname 'golbez' 
Apr  2 09:33:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  2 09:33:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  2 09:33:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  2 09:33:29 golbez avahi-daemon[5766]: Withdrawing address record for 192.168.4.100 on wlan0.
Apr  2 09:33:29 golbez avahi-daemon[5766]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.4.100.
Apr  2 09:33:29 golbez avahi-daemon[5766]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  2 09:33:29 golbez avahi-daemon[5766]: Withdrawing address record for fe80::21a:73ff:fe7f:13f1 on wlan0.
Apr  2 09:33:29 golbez avahi-daemon[5766]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.4.100.
Apr  2 09:33:29 golbez avahi-daemon[5766]: New relevant interface wlan0.IPv4 for mDNS.
Apr  2 09:33:29 golbez avahi-daemon[5766]: Registering new address record for 192.168.4.100 on wlan0.IPv4.
Apr  2 09:33:30 golbez NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  2 09:33:30 golbez NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  2 09:33:30 golbez NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Apr  2 09:33:30 golbez NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  2 09:33:30 golbez NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Apr  2 09:33:31 golbez avahi-daemon[5766]: Registering new address record for fe80::21a:73ff:fe7f:13f1 on wlan0.*.
Apr  2 09:33:41 golbez kernel: [49334.088000] wlan0: no IPv6 routers present
Apr  2 09:34:10 golbez ntpdate[11897]: can't find host ntp.ubuntu.com 
Apr  2 09:34:10 golbez ntpdate[11897]: no servers can be used, exiting
Apr  2 09:35:07 golbez NetworkManager: <info>  SWITCH: terminating current connection 'wlan0' because it's no longer valid. 
Apr  2 09:35:07 golbez NetworkManager: <info>  Deactivating device wlan0. 
Apr  2 09:35:07 golbez dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 11833
Apr  2 09:35:07 golbez dhclient: killed old client process, removed PID file
Apr  2 09:35:07 golbez dhclient: DHCPRELEASE on wlan0 to 192.168.4.1 port 67
Apr  2 09:35:07 golbez avahi-daemon[5766]: Withdrawing address record for 192.168.4.100 on wlan0.
Apr  2 09:35:07 golbez avahi-daemon[5766]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.4.100.
Apr  2 09:35:08 golbez avahi-daemon[5766]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  2 09:35:08 golbez avahi-daemon[5766]: Withdrawing address record for fe80::21a:73ff:fe7f:13f1 on wlan0.
Apr  2 09:35:08 golbez NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Apr  2 09:35:08 golbez NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Apr  2 09:35:08 golbez NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Apr  2 09:35:16 golbez NetworkManager: <debug> [1207143316.865511] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Ottawa' 
Apr  2 09:35:16 golbez NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Ottawa 
Apr  2 09:35:16 golbez NetworkManager: <info>  Deactivating device wlan0. 
Apr  2 09:35:16 golbez NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Apr  2 09:35:16 golbez NetworkManager: <info>  Device wlan0 activation scheduled... 
Apr  2 09:35:16 golbez NetworkManager: <info>  Activation (wlan0) started... 
Apr  2 09:35:16 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  2 09:35:16 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr  2 09:35:16 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  2 09:35:16 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr  2 09:35:16 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr  2 09:35:16 golbez NetworkManager: <info>  Activation (wlan0/wireless): access point 'Ottawa' is encrypted, and a key exists.  No new key needed. 
Apr  2 09:35:16 golbez kernel: [49429.980000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  2 09:35:17 golbez NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Apr  2 09:35:18 golbez NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant5^I' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:35:18 golbez NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: response was '0' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4f7474617761' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr  2 09:35:18 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:35:18 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 09:35:21 golbez NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Ottawa'. 
Apr  2 09:35:21 golbez NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  2 09:35:21 golbez NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Apr  2 09:35:21 golbez kernel: [49434.916000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  2 09:35:22 golbez NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Apr  2 09:35:22 golbez NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  2 09:35:22 golbez NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Apr  2 09:35:22 golbez dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Apr  2 09:35:23 golbez avahi-daemon[5766]: Registering new address record for fe80::21a:73ff:fe7f:13f1 on wlan0.*.
Apr  2 09:35:23 golbez NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Apr  2 09:35:26 golbez dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr  2 09:35:27 golbez dhclient: DHCPOFFER from 192.168.4.1
Apr  2 09:35:27 golbez dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Apr  2 09:35:27 golbez dhclient: DHCPACK from 192.168.4.1
Apr  2 09:35:27 golbez avahi-daemon[5766]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.4.100.
Apr  2 09:35:27 golbez avahi-daemon[5766]: New relevant interface wlan0.IPv4 for mDNS.
Apr  2 09:35:27 golbez avahi-daemon[5766]: Registering new address record for 192.168.4.100 on wlan0.IPv4.
Apr  2 09:35:27 golbez NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Apr  2 09:35:27 golbez NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  2 09:35:27 golbez NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Apr  2 09:35:27 golbez dhclient: bound to 192.168.4.100 -- renewal in 40473 seconds.
Apr  2 09:35:28 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Apr  2 09:35:28 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Apr  2 09:35:28 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Apr  2 09:35:28 golbez NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  2 09:35:28 golbez NetworkManager: <info>    address 192.168.4.100 
Apr  2 09:35:28 golbez NetworkManager: <info>    netmask 255.255.255.0 
Apr  2 09:35:28 golbez NetworkManager: <info>    broadcast 192.168.4.255 
Apr  2 09:35:28 golbez NetworkManager: <info>    gateway 192.168.4.1 
Apr  2 09:35:28 golbez NetworkManager: <info>    nameserver 206.47.244.101 
Apr  2 09:35:28 golbez NetworkManager: <info>    nameserver 206.47.244.102 
Apr  2 09:35:28 golbez NetworkManager: <info>    hostname 'golbez' 
Apr  2 09:35:28 golbez NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  2 09:35:28 golbez NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  2 09:35:28 golbez NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  2 09:35:28 golbez avahi-daemon[5766]: Withdrawing address record for 192.168.4.100 on wlan0.
Apr  2 09:35:28 golbez avahi-daemon[5766]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.4.100.
Apr  2 09:35:28 golbez avahi-daemon[5766]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  2 09:35:28 golbez avahi-daemon[5766]: Withdrawing address record for fe80::21a:73ff:fe7f:13f1 on wlan0.
Apr  2 09:35:28 golbez avahi-daemon[5766]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.4.100.
Apr  2 09:35:28 golbez avahi-daemon[5766]: New relevant interface wlan0.IPv4 for mDNS.
Apr  2 09:35:28 golbez avahi-daemon[5766]: Registering new address record for 192.168.4.100 on wlan0.IPv4.
Apr  2 09:35:29 golbez NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  2 09:35:29 golbez NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  2 09:35:29 golbez NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Apr  2 09:35:29 golbez NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Apr  2 09:35:29 golbez NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  2 09:35:30 golbez avahi-daemon[5766]: Registering new address record for fe80::21a:73ff:fe7f:13f1 on wlan0.*.
Apr  2 09:35:39 golbez kernel: [49452.708000] wlan0: no IPv6 routers present
Apr  2 09:36:09 golbez ntpdate[12025]: can't find host ntp.ubuntu.com 
Apr  2 09:36:09 golbez ntpdate[12025]: no servers can be used, exiting
Apr  2 09:38:36 golbez kernel: [49629.588000] eth0: link up.
Apr  2 09:38:36 golbez kernel: [49629.592000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  2 09:38:38 golbez avahi-daemon[5766]: Registering new address record for fe80::21b:24ff:fe7a:48b4 on eth0.*.
Apr  2 09:38:47 golbez kernel: [49640.588000] eth0: no IPv6 routers present
Apr  2 09:39:01 golbez /USR/SBIN/CRON[12045]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  2 09:52:10 golbez -- MARK --
Apr  2 09:58:12 golbez NetworkManager: <debug> [1207144692.380163] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Gatineau' 
Apr  2 09:58:12 golbez NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Gatineau 
Apr  2 09:58:12 golbez NetworkManager: <info>  Deactivating device wlan0. 
Apr  2 09:58:12 golbez dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 11963
Apr  2 09:58:12 golbez dhclient: killed old client process, removed PID file
Apr  2 09:58:12 golbez dhclient: DHCPRELEASE on wlan0 to 192.168.4.1 port 67
Apr  2 09:58:12 golbez avahi-daemon[5766]: Withdrawing address record for 192.168.4.100 on wlan0.
Apr  2 09:58:12 golbez avahi-daemon[5766]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.4.100.
Apr  2 09:58:12 golbez avahi-daemon[5766]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  2 09:58:13 golbez avahi-daemon[5766]: Withdrawing address record for fe80::21a:73ff:fe7f:13f1 on wlan0.
Apr  2 09:58:13 golbez NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Apr  2 09:58:13 golbez NetworkManager: <info>  Device wlan0 activation scheduled... 
Apr  2 09:58:13 golbez NetworkManager: <info>  Activation (wlan0) started... 
Apr  2 09:58:13 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  2 09:58:13 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr  2 09:58:13 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  2 09:58:13 golbez NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr  2 09:58:13 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr  2 09:58:13 golbez NetworkManager: <info>  Activation (wlan0/wireless): access point 'Gatineau' is encrypted, and a key exists.  No new key needed. 
Apr  2 09:58:14 golbez NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Apr  2 09:58:14 golbez NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant7^I' 
Apr  2 09:58:14 golbez kernel: [50807.660000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:58:14 golbez NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: response was '0' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 476174696e656175' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr  2 09:58:14 golbez NetworkManager: <info>  SUP: response was 'OK' 
Apr  2 09:58:14 golbez NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 09:58:18 golbez NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Gatineau'. 
Apr  2 09:58:18 golbez NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  2 09:58:18 golbez NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Apr  2 09:58:18 golbez kernel: [50811.344000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  2 09:58:19 golbez NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Apr  2 09:58:19 golbez NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  2 09:58:19 golbez NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Apr  2 09:58:19 golbez dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Apr  2 09:58:19 golbez avahi-daemon[5766]: Registering new address record for fe80::21a:73ff:fe7f:13f1 on wlan0.*.
Apr  2 09:58:20 golbez NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Apr  2 09:58:21 golbez dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr  2 09:58:21 golbez dhclient: DHCPOFFER from 192.168.1.2
Apr  2 09:58:21 golbez dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Apr  2 09:58:21 golbez dhclient: DHCPACK from 192.168.1.2
Apr  2 09:58:21 golbez avahi-daemon[5766]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.70.
Apr  2 09:58:21 golbez avahi-daemon[5766]: New relevant interface wlan0.IPv4 for mDNS.
Apr  2 09:58:21 golbez avahi-daemon[5766]: Registering new address record for 192.168.1.70 on wlan0.IPv4.
Apr  2 09:58:21 golbez NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Apr  2 09:58:21 golbez NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  2 09:58:21 golbez NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Apr  2 09:58:21 golbez dhclient: bound to 192.168.1.70 -- renewal in 294195 seconds.
Apr  2 09:58:21 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Apr  2 09:58:21 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Apr  2 09:58:21 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Apr  2 09:58:21 golbez dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Apr  2 09:58:21 golbez NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  2 09:58:21 golbez NetworkManager: <info>    address 192.168.1.70 
Apr  2 09:58:21 golbez NetworkManager: <info>    netmask 255.255.255.0 
Apr  2 09:58:21 golbez NetworkManager: <info>    broadcast 192.168.1.255 
Apr  2 09:58:21 golbez NetworkManager: <info>    gateway 192.168.1.251 
Apr  2 09:58:21 golbez NetworkManager: <info>    nameserver 192.168.1.251 
Apr  2 09:58:21 golbez NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  2 09:58:21 golbez NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  2 09:58:21 golbez NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  2 09:58:21 golbez avahi-daemon[5766]: Withdrawing address record for 192.168.1.70 on wlan0.
Apr  2 09:58:21 golbez avahi-daemon[5766]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.70.
Apr  2 09:58:21 golbez avahi-daemon[5766]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  2 09:58:21 golbez avahi-daemon[5766]: Withdrawing address record for fe80::21a:73ff:fe7f:13f1 on wlan0.
Apr  2 09:58:21 golbez avahi-daemon[5766]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.70.
Apr  2 09:58:21 golbez avahi-daemon[5766]: New relevant interface wlan0.IPv4 for mDNS.
Apr  2 09:58:21 golbez avahi-daemon[5766]: Registering new address record for 192.168.1.70 on wlan0.IPv4.
Apr  2 09:58:22 golbez NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  2 09:58:22 golbez NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  2 09:58:22 golbez NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Apr  2 09:58:22 golbez NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  2 09:58:22 golbez NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Apr  2 09:58:18 golbez ntpdate[12196]: step time server 91.189.94.4 offset -4.487980 sec
Apr  2 09:58:19 golbez avahi-daemon[5766]: Registering new address record for fe80::21a:73ff:fe7f:13f1 on wlan0.*.
Apr  2 09:58:28 golbez kernel: [50825.792000] wlan0: no IPv6 routers present
Apr  2 10:09:01 golbez /USR/SBIN/CRON[12257]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  2 10:17:01 golbez /USR/SBIN/CRON[12453]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

Now that I look at it, I'm getting a lot of strange messages from my wireless card. I'll look at that, but if you have any insights, please let me know.

Thanks in advance!

J-F

---

### Post by jfbilodeau on 2008-04-05
I think I found the problem :(

My SATA drive is on its last leg and is causing no end of grief to my root partition.

However, on the upside, it shows that even with a corrupted root, Linux continued to work (albeit slowly). It's not the first time I've seen Linux continue to function normally even though the disk was full/corrupted/missing ;)

J-F

---

