---
title: "X Doesn't Start, Can't Restart System"
date: 2006-11-10
forum: General Help
---

### Post by JPMaximilian on 2006-11-10
I've got some problems that started when I reconfigured my xorg.conf.  The first is that when I start my computer, it hangs when X is loading, so I have to do ctrl, alt, backspace, I get to a command line where I can login and then if I type "startx" x loads fine.  The other problem is that once I'm to a desktop, when I click on the icon for logging out, restarting etc, normally there are 6 some options, log out, lock screen, switch user, shutdown, restart and hibernate.  Only for some reason, the shutdown and restart buttons are missing.  So I have to manually shutdown in the command line.  

Any help in resolving these issues would be appreciated.

---

### Post by bigken on 2006-11-10
try running sudo dpkg-reconfigure xserver-xorg

---

### Post by elettronicha on 2006-11-10
> **JPMaximilian said:**
> I've got some problems that started when I reconfigured my xorg.conf.  The first is that when I start my computer, it hangs when X is loading, so I have to do ctrl, alt, backspace, I get to a command line where I can login and then if I type "startx" x loads fine.
What did you do when you reconfigured xorg.conf?
Some infos about your system (e.g. graphic card,...)?
Also attach /var/log/Xorg.0.log, and the parts of /var/log/syslog and /var/log/kern.log related to the time of crashes.

> The other problem is that once I'm to a desktop, when I click on the icon for logging out, restarting etc, normally there are 6 some options, log out, lock screen, switch user, shutdown, restart and hibernate.  Only for some reason, the shutdown and restart buttons are missing.  So I have to manually shutdown in the command line.
That's obvious, since you started the X server from a console login, your graphical login manager (GDM, KDM, ...) didn't start and can't handle reboot/shutdown. So you can do that operation only from where you logged in.

---

### Post by JPMaximilian on 2006-11-13
From the kern.log there are many many lines like these:

Nov  7 08:01:26 localhost kernel: [17209074.760000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08d24000 for 65536 bytes
Nov  7 08:01:26 localhost kernel: [17209074.900000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov  7 08:01:26 localhost kernel: [17209074.900000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc97d7300 for 65536 bytes
Nov  7 08:01:26 localhost kernel: [17209074.900000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08d24000 for 65536 bytes
Nov  7 08:01:26 localhost kernel: [17209074.904000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov  7 08:01:26 localhost kernel: [17209074.904000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xcb14a7c0 for 65536 bytes
Nov  7 08:01:26 localhost kernel: [17209074.904000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08d24000 for 65536 bytes

The forum won't let me attach the other files you asked for.

---

### Post by elettronicha on 2006-11-13
Just after you get a running desktop environment open a terminal and type

cat /var/log/Xorg.0.log > xorg0-log.txt
cat /var/log/syslog > syslog.txt
cat /var/log/kern.log > kernlog.txt

Then attach the .txt files. From those lines you posted, it seems something went wrong when you installed the proprietary ATI drivers or when you reconfigured xorg.conf.

---

### Post by JPMaximilian on 2006-11-13
All those log files end up being much more than the maximum 19.5 KB allowed for TXT files, so I can't attach the logs.  ](*,)

---

### Post by elettronicha on 2006-11-13
Ok, just post the files between the 'code' tags, then.

---

### Post by JPMaximilian on 2006-11-13
If I use the fglrx driver, everything boots fine, but I don't want to use this driver because when I drag icons or items on the panel, they get all distorted.

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

When I run the reconfiguration tool, it defaults back to ati, so this might be the problem.  I'll run the config once more and then post the logs.

---

### Post by JPMaximilian on 2006-11-13
SysLog:

Nov 13 12:50:30 localhost kernel: [17191332.736000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2a7f000 for 4096000 bytes
Nov 13 12:50:30 localhost kernel: [17191332.760000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:30 localhost kernel: [17191332.760000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xcddc5580 for 4096000 bytes
Nov 13 12:50:34 localhost kernel: [17191336.412000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2a7f000 for 4096000 bytes
Nov 13 12:50:34 localhost kernel: [17191336.432000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:34 localhost kernel: [17191336.432000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xcacb7c00 for 4096000 bytes
Nov 13 12:50:35 localhost kernel: [17191337.864000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2a7f000 for 4096000 bytes
Nov 13 12:50:35 localhost kernel: [17191337.888000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:35 localhost kernel: [17191337.888000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc0d86c80 for 4096000 bytes
Nov 13 12:50:53 localhost gconfd (john-5653): GConf server is not in use, shutting down.
Nov 13 12:50:53 localhost gconfd (john-5653): Exiting
Nov 13 12:52:32 localhost gconfd (john-6109): starting (version 2.14.0), pid 6109 user 'john'
Nov 13 12:52:32 localhost gconfd (john-6109): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov 13 12:52:32 localhost gconfd (john-6109): Resolved address "xml:readwrite:/home/john/.gconf" to a writable configuration source at position 1
Nov 13 12:52:32 localhost gconfd (john-6109): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 13 12:52:32 localhost gconfd (john-6109): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov 13 12:52:32 localhost gconfd (john-6109): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 13 12:52:33 localhost gconfd (john-6109): Resolved address "xml:readwrite:/home/john/.gconf" to a writable configuration source at position 0
Nov 13 12:53:02 localhost gconfd (john-6109): Exiting
Nov 13 12:53:09 localhost shutdown[6208]: shutting down for system reboot
Nov 13 12:53:09 localhost init: Switching to runlevel: 6
Nov 13 12:53:22 localhost kernel: [17191504.408000] apm: BIOS not found.
Nov 13 12:53:26 localhost ntpd[4542]: ntpd exiting on signal 15
Nov 13 12:53:28 localhost sdpd[4562]: terminating...   
Nov 13 12:53:28 localhost hcid[4558]: Exit.
Nov 13 12:53:28 localhost kernel: Kernel logging (proc) stopped.
Nov 13 12:53:28 localhost kernel: Kernel log daemon terminating.
Nov 13 12:53:28 localhost exiting on signal 15
Nov 13 12:54:17 localhost syslogd 1.4.1#17ubuntu7: restart.
Nov 13 12:54:18 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386
Nov 13 12:54:18 localhost kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Nov 13 12:54:18 localhost kernel: Symbols match kernel version 2.6.15.
Nov 13 12:54:18 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Nov 13 12:54:18 localhost kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
Nov 13 12:54:18 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000000dea0000 (usable)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 000000000dea0000 - 000000000deab000 (ACPI data)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 000000000deab000 - 000000000df00000 (ACPI NVS)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 000000000df00000 - 000000000e000000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000] 0MB HIGHMEM available.
Nov 13 12:54:18 localhost kernel: [17179569.184000] 222MB LOWMEM available.
Nov 13 12:54:18 localhost kernel: [17179569.184000] found SMP MP-table at 000f8620
Nov 13 12:54:18 localhost kernel: [17179569.184000] On node 0 totalpages: 56992
Nov 13 12:54:18 localhost kernel: [17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
Nov 13 12:54:18 localhost kernel: [17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
Nov 13 12:54:18 localhost kernel: [17179569.184000]   Normal zone: 52896 pages, LIFO batch:15
Nov 13 12:54:18 localhost kernel: [17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
Nov 13 12:54:18 localhost kernel: [17179569.184000] DMI present.
Nov 13 12:54:18 localhost kernel: [17179569.184000] ATI board detected. Disabling timer routing over 8254.
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f85f0
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0dea405e
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: FADT (v001 ATI    Bonefish 0x06040000 ATI  0x000f4240) @ 0x0deaaeb0
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x0deaaf24
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x0deaaf74
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x0deaafc4
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050228) @ 0x0dea45cf
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x0dea409a
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: DSDT (v001    ATI    SB450 0x06040000 MSFT 0x0100000e) @ 0x00000000
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x8008
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: Local APIC address 0xfee00000
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: 2 duplicate APIC table ignored.
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Processor #0 6:14 APIC version 20
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov 13 12:54:18 localhost kernel: [17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 13 12:54:18 localhost kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Nov 13 12:54:18 localhost kernel: [17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0e000000:f0c00000)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Built 1 zonelists
Nov 13 12:54:18 localhost kernel: [17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
Nov 13 12:54:18 localhost kernel: [17179569.184000] mapped APIC to ffffd000 (fee00000)
Nov 13 12:54:18 localhost kernel: [17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Initializing CPU#0
Nov 13 12:54:18 localhost kernel: [17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Detected 1463.201 MHz processor.
Nov 13 12:54:18 localhost kernel: [17179569.184000] Using pmtmr for high-res timesource
Nov 13 12:54:18 localhost kernel: [17179569.184000] Console: colour VGA+ 80x25
Nov 13 12:54:18 localhost kernel: [17179570.056000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 13 12:54:18 localhost kernel: [17179570.056000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Nov 13 12:54:18 localhost kernel: [17179570.060000] Memory: 215468k/227968k available (1976k kernel code, 11896k reserved, 606k data, 288k init, 0k highmem)
Nov 13 12:54:18 localhost kernel: [17179570.060000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 13 12:54:18 localhost kernel: [17179570.140000] Calibrating delay using timer specific routine.. 2931.33 BogoMIPS (lpj=5862674)
Nov 13 12:54:18 localhost kernel: [17179570.140000] Security Framework v1.0.0 initialized
Nov 13 12:54:18 localhost kernel: [17179570.140000] SELinux:  Disabled at boot.
Nov 13 12:54:18 localhost kernel: [17179570.140000] Mount-cache hash table entries: 512
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
Nov 13 12:54:18 localhost kernel: [17179570.140000] monitor/mwait feature present.
Nov 13 12:54:18 localhost kernel: [17179570.140000] using mwait in idle threads.
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: L2 cache: 1024K
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 0000c109 00000000 00000000
Nov 13 12:54:18 localhost kernel: [17179570.140000] mtrr: v2.0 (20020519)
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
Nov 13 12:54:18 localhost kernel: [17179570.140000] Enabling fast FPU save and restore... done.
Nov 13 12:54:18 localhost kernel: [17179570.140000] Enabling unmasked SIMD FPU exception support... done.
Nov 13 12:54:18 localhost kernel: [17179570.140000] Checking 'hlt' instruction... OK.
Nov 13 12:54:18 localhost kernel: [17179570.156000] checking if image is initramfs... it is
Nov 13 12:54:18 localhost kernel: [17179570.888000] Freeing initrd memory: 6617k freed
Nov 13 12:54:18 localhost kernel: [17179570.920000] ACPI: Looking for DSDT ... not found!
Nov 13 12:54:18 localhost kernel: [17179571.332000] ENABLING IO-APIC IRQs
Nov 13 12:54:18 localhost kernel: [17179571.332000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov 13 12:54:18 localhost kernel: [17179571.476000] NET: Registered protocol family 16
Nov 13 12:54:18 localhost kernel: [17179571.476000] EISA bus registered
Nov 13 12:54:18 localhost kernel: [17179571.476000] ACPI: bus type pci registered
Nov 13 12:54:18 localhost kernel: [17179571.476000] PCI: BIOS BUG #81[49435024] found
Nov 13 12:54:18 localhost kernel: [17179571.476000] PCI: Using MMCONFIG
Nov 13 12:54:18 localhost kernel: [17179571.476000] ACPI: Subsystem revision 20051216
Nov 13 12:54:18 localhost kernel: [17179571.480000] ACPI: Interpreter enabled
Nov 13 12:54:18 localhost kernel: [17179571.480000] ACPI: Using IOAPIC for interrupt routing
Nov 13 12:54:18 localhost kernel: [17179571.480000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 13 12:54:18 localhost kernel: [17179571.480000] PCI: Probing PCI hardware (bus 00)
Nov 13 12:54:18 localhost kernel: [17179571.484000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
Nov 13 12:54:18 localhost kernel: [17179571.484000] Boot video device is 0000:01:05.0
Nov 13 12:54:18 localhost kernel: [17179571.484000] PCI: Transparent bridge - 0000:00:14.4
Nov 13 12:54:18 localhost kernel: [17179571.484000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.488000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.488000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.488000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.488000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: Embedded Controller [EC0] (gpe 3) interrupt mode.
Nov 13 12:54:18 localhost kernel: [17179571.548000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.548000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.552000] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: PnP ACPI init
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: PnP ACPI: found 9 devices
Nov 13 12:54:18 localhost kernel: [17179571.552000] PnPBIOS: Disabled by ACPI PNP
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Using ACPI for IRQ routing
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: 00:05: ioport range 0x1080-0x1080 has been reserved
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: 00:05: ioport range 0x220-0x22f has been reserved
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: 00:05: ioport range 0x40b-0x40b has been reserved
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: 00:05: ioport range 0x4d0-0x4d1 has been reserved
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Bridge: 0000:00:01.0
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: 9000-9fff
Nov 13 12:54:18 localhost kernel: [17179571.552000]   MEM window: d0100000-d01fffff
Nov 13 12:54:18 localhost kernel: [17179571.552000]   PREFETCH window: d4000000-d7ffffff
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Bridge: 0000:00:04.0
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000]   MEM window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000]   PREFETCH window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Bridge: 0000:00:06.0
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000]   MEM window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000]   PREFETCH window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Bus 11, cardbus bridge: 0000:0a:00.0
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: 0000a400-0000a4ff
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: 0000a800-0000a8ff
Nov 13 12:54:18 localhost kernel: [17179571.552000]   PREFETCH window: 10000000-11ffffff
Nov 13 12:54:18 localhost kernel: [17179571.556000]   MEM window: 12000000-13ffffff
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Bridge: 0000:00:14.4
Nov 13 12:54:18 localhost kernel: [17179571.556000]   IO window: a000-afff
Nov 13 12:54:18 localhost kernel: [17179571.556000]   MEM window: d0200000-d02fffff
Nov 13 12:54:18 localhost kernel: [17179571.556000]   PREFETCH window: 10000000-11ffffff
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 13 12:54:18 localhost kernel: [17179571.556000] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 22 (level, low) -> IRQ 185
Nov 13 12:54:18 localhost kernel: [17179571.556000] audit: initializing netlink socket (disabled)
Nov 13 12:54:18 localhost kernel: [17179571.556000] audit(1163422435.556:1): initialized
Nov 13 12:54:18 localhost kernel: [17179571.556000] VFS: Disk quotas dquot_6.5.1
Nov 13 12:54:18 localhost kernel: [17179571.556000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 13 12:54:18 localhost kernel: [17179571.556000] Initializing Cryptographic API
Nov 13 12:54:18 localhost kernel: [17179571.556000] io scheduler noop registered
Nov 13 12:54:18 localhost kernel: [17179571.556000] io scheduler anticipatory registered
Nov 13 12:54:18 localhost kernel: [17179571.556000] io scheduler deadline registered
Nov 13 12:54:18 localhost kernel: [17179571.556000] io scheduler cfq registered
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 13 12:54:18 localhost kernel: [17179571.556000] pcie_portdrv_probe->Dev[5a36:1002] has invalid IRQ. Check vendor BIOS
Nov 13 12:54:18 localhost kernel: [17179571.556000] assign_interrupt_mode Found MSI capability
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie00]
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie01]
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie03]
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 13 12:54:18 localhost kernel: [17179571.556000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
Nov 13 12:54:18 localhost kernel: [17179571.556000] assign_interrupt_mode Found MSI capability
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie00]
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie01]
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie03]
Nov 13 12:54:18 localhost kernel: [17179571.556000] isapnp: Scanning for PnP cards...
Nov 13 12:54:18 localhost kernel: [17179571.912000] isapnp: No Plug & Play device found
Nov 13 12:54:18 localhost kernel: [17179571.928000] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov 13 12:54:18 localhost kernel: [17179571.928000] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 13 12:54:18 localhost kernel: [17179571.928000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Nov 13 12:54:18 localhost kernel: [17179571.932000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 13 12:54:18 localhost kernel: [17179571.932000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 13 12:54:18 localhost kernel: [17179571.932000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 13 12:54:18 localhost kernel: [17179571.932000] mice: PS/2 mouse device common for all mice
Nov 13 12:54:18 localhost kernel: [17179571.932000] EISA: Probing bus 0 at eisa.0
Nov 13 12:54:18 localhost kernel: [17179571.932000] Cannot allocate resource for EISA slot 1
Nov 13 12:54:18 localhost kernel: [17179571.932000] Cannot allocate resource for EISA slot 8
Nov 13 12:54:18 localhost kernel: [17179571.932000] EISA: Detected 0 cards.
Nov 13 12:54:18 localhost kernel: [17179571.932000] NET: Registered protocol family 2
Nov 13 12:54:18 localhost kernel: [17179571.972000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP: Hash tables configured (established 8192 bind 8192)
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP reno registered
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP bic registered
Nov 13 12:54:18 localhost kernel: [17179571.972000] NET: Registered protocol family 1
Nov 13 12:54:18 localhost kernel: [17179571.972000] NET: Registered protocol family 8
Nov 13 12:54:18 localhost kernel: [17179571.972000] NET: Registered protocol family 20
Nov 13 12:54:18 localhost kernel: [17179571.972000] Using IPI Shortcut mode
Nov 13 12:54:18 localhost kernel: [17179571.972000] ACPI wakeup devices: 
Nov 13 12:54:18 localhost kernel: [17179571.972000] LID0 SLPB  PB2  PB3  PB4  PB6  PB7 OHC1 OHC2 EHCI  P2P AZLA 
Nov 13 12:54:18 localhost kernel: [17179571.972000] ACPI: (supports S0 S3 S4 S5)
Nov 13 12:54:18 localhost kernel: [17179571.972000] Freeing unused kernel memory: 288k freed
Nov 13 12:54:18 localhost kernel: [17179572.020000] vga16fb: initializing
Nov 13 12:54:18 localhost kernel: [17179572.020000] vga16fb: mapped to 0xc00a0000
Nov 13 12:54:18 localhost kernel: [17179572.112000] Console: switching to colour frame buffer device 80x25
Nov 13 12:54:18 localhost kernel: [17179572.112000] fb0: VGA16 VGA frame buffer device
Nov 13 12:54:18 localhost kernel: [17179572.536000] input: AT Translated Set 2 keyboard as /class/input/input0
Nov 13 12:54:18 localhost kernel: [17179573.232000] Capability LSM initialized
Nov 13 12:54:18 localhost kernel: [17179573.268000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Nov 13 12:54:18 localhost kernel: [17179573.268000] ACPI: Processor [CPU0] (supports 8 throttling states)
Nov 13 12:54:18 localhost kernel: [17179573.324000] ACPI: Thermal Zone [TZS0] (48 C)
Nov 13 12:54:18 localhost kernel: [17179573.380000] ACPI: Thermal Zone [TZS1] (49 C)
Nov 13 12:54:18 localhost kernel: [17179573.828000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
Nov 13 12:54:18 localhost kernel: [17179573.828000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 217
Nov 13 12:54:18 localhost kernel: [17179573.828000] ATIIXP: chipset revision 128
Nov 13 12:54:18 localhost kernel: [17179573.828000] ATIIXP: not 100%% native mode: will probe irqs later
Nov 13 12:54:18 localhost kernel: [17179573.828000]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:DMA, hdb:DMA
Nov 13 12:54:18 localhost kernel: [17179573.828000] ATIIXP: simplex device: DMA disabled
Nov 13 12:54:18 localhost kernel: [17179573.828000] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
Nov 13 12:54:18 localhost kernel: [17179573.828000] Probing IDE interface ide0...
Nov 13 12:54:18 localhost kernel: [17179574.116000] hda: Hitachi IC25N060ATMR04-0, ATA DISK drive
Nov 13 12:54:18 localhost kernel: [17179574.900000] hdb: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, ATAPI CD/DVD-ROM drive
Nov 13 12:54:18 localhost kernel: [17179574.956000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov 13 12:54:18 localhost kernel: [17179574.980000] Probing IDE interface ide1...
Nov 13 12:54:18 localhost kernel: [17179575.548000] hda: max request size: 1024KiB
Nov 13 12:54:18 localhost kernel: [17179575.556000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
Nov 13 12:54:18 localhost kernel: [17179575.556000] hda: cache flushes supported
Nov 13 12:54:18 localhost kernel: [17179575.556000]  hda: hda1 hda2 < hda5 >
Nov 13 12:54:18 localhost kernel: [17179575.608000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Nov 13 12:54:18 localhost kernel: [17179575.608000] Uniform CD-ROM driver Revision: 3.20
Nov 13 12:54:18 localhost kernel: [17179576.052000] usbcore: registered new driver usbfs
Nov 13 12:54:18 localhost kernel: [17179576.052000] usbcore: registered new driver hub
Nov 13 12:54:18 localhost kernel: [17179576.052000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Nov 13 12:54:18 localhost kernel: [17179576.052000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 225
Nov 13 12:54:18 localhost kernel: [17179576.052000] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 13 12:54:18 localhost kernel: [17179576.056000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Nov 13 12:54:18 localhost kernel: [17179576.056000] ohci_hcd 0000:00:13.0: irq 225, io mem 0xd0005000
Nov 13 12:54:18 localhost kernel: [17179576.064000] hub 1-0:1.0: USB hub found
Nov 13 12:54:18 localhost kernel: [17179576.064000] hub 1-0:1.0: 4 ports detected
Nov 13 12:54:18 localhost kernel: [17179576.168000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 225
Nov 13 12:54:18 localhost kernel: [17179576.168000] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 13 12:54:18 localhost kernel: [17179576.168000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Nov 13 12:54:18 localhost kernel: [17179576.168000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xd0006000
Nov 13 12:54:18 localhost kernel: [17179576.172000] hub 2-0:1.0: USB hub found
Nov 13 12:54:18 localhost kernel: [17179576.172000] hub 2-0:1.0: 4 ports detected
Nov 13 12:54:18 localhost kernel: [17179576.276000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 225
Nov 13 12:54:18 localhost kernel: [17179576.276000] ehci_hcd 0000:00:13.2: EHCI Host Controller
Nov 13 12:54:18 localhost kernel: [17179576.276000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Nov 13 12:54:18 localhost kernel: [17179576.276000] ehci_hcd 0000:00:13.2: irq 225, io mem 0xd0007000
Nov 13 12:54:18 localhost kernel: [17179576.276000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 13 12:54:18 localhost kernel: [17179576.276000] hub 3-0:1.0: USB hub found
Nov 13 12:54:18 localhost kernel: [17179576.276000] hub 3-0:1.0: 8 ports detected
Nov 13 12:54:18 localhost kernel: [17179576.392000] Probing IDE interface ide1...
Nov 13 12:54:18 localhost kernel: [17179576.868000] usb 1-1: new low speed USB device using ohci_hcd and address 3
Nov 13 12:54:18 localhost kernel: [17179577.056000] Attempting manual resume
Nov 13 12:54:18 localhost kernel: [17179577.088000] usbcore: registered new driver hiddev
Nov 13 12:54:18 localhost kernel: [17179577.096000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
Nov 13 12:54:18 localhost kernel: [17179577.096000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1
Nov 13 12:54:18 localhost kernel: [17179577.096000] usbcore: registered new driver usbhid
Nov 13 12:54:18 localhost kernel: [17179577.096000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Nov 13 12:54:18 localhost kernel: [17179577.144000] EXT3-fs: mounted filesystem with ordered data mode.
Nov 13 12:54:18 localhost kernel: [17179577.156000] kjournald starting.  Commit interval 5 seconds
Nov 13 12:54:18 localhost kernel: [17179583.232000] ts: Compaq touchscreen protocol output
Nov 13 12:54:18 localhost kernel: [17179584.612000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 13 12:54:18 localhost kernel: [17179584.616000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 13 12:54:18 localhost kernel: [17179584.948000] Linux agpgart interface v0.101 (c) Dave Jones
Nov 13 12:54:18 localhost kernel: [17179585.344000] Real Time Clock Driver v1.12
Nov 13 12:54:18 localhost kernel: [17179585.380000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 217
Nov 13 12:54:18 localhost kernel: [17179585.492000] input: PC Speaker as /class/input/input2
Nov 13 12:54:18 localhost kernel: [17179585.872000] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 22 (level, low) -> IRQ 185
Nov 13 12:54:18 localhost kernel: [17179585.872000] Yenta: CardBus bridge found at 0000:0a:00.0 [1025:0080]
Nov 13 12:54:18 localhost kernel: [17179585.872000] Yenta: Using CSCINT to route CSC interrupts to PCI
Nov 13 12:54:18 localhost kernel: [17179585.872000] Yenta: Routing CardBus interrupts to PCI
Nov 13 12:54:18 localhost kernel: [17179585.872000] Yenta TI: socket 0000:0a:00.0, mfunc 0x01aa1b22, devctl 0x44
Nov 13 12:54:18 localhost kernel: [17179585.928000] 8139too Fast Ethernet driver 0.9.27
Nov 13 12:54:18 localhost kernel: [17179586.044000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x204000
Nov 13 12:54:18 localhost kernel: [17179586.068000] ath_hal: module license 'Proprietary' taints kernel.
Nov 13 12:54:18 localhost kernel: [17179586.068000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
Nov 13 12:54:18 localhost kernel: [17179586.076000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Nov 13 12:54:18 localhost kernel: [17179586.080000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Nov 13 12:54:18 localhost kernel: [17179586.104000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
Nov 13 12:54:18 localhost kernel: [17179586.104000] Socket status: 30000006
Nov 13 12:54:18 localhost kernel: [17179586.104000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0c to #0e
Nov 13 12:54:18 localhost kernel: [17179586.104000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
Nov 13 12:54:18 localhost kernel: [17179586.104000] cs: IO port probe 0xa000-0xafff: clean.
Nov 13 12:54:18 localhost kernel: [17179586.104000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
Nov 13 12:54:18 localhost kernel: [17179586.104000] pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x11ffffff
Nov 13 12:54:18 localhost kernel: [17179586.120000] ACPI: PCI Interrupt 0000:0a:01.0[A] -> GSI 20 (level, low) -> IRQ 50
Nov 13 12:54:18 localhost kernel: [17179586.120000] eth0: RealTek RTL8139 at 0xce9bc000, 00:16:d3:42:8a:f5, IRQ 50
Nov 13 12:54:18 localhost kernel: [17179586.120000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Nov 13 12:54:18 localhost kernel: [17179586.140000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Nov 13 12:54:18 localhost kernel: [17179586.204000] wlan: 0.8.6.0 (EXPERIMENTAL)
Nov 13 12:54:18 localhost kernel: [17179586.208000] ath_rate_sample: 1.2
Nov 13 12:54:18 localhost kernel: [17179586.228000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
Nov 13 12:54:18 localhost kernel: [17179586.228000] ACPI: PCI Interrupt 0000:0a:06.0[A] -> GSI 23 (level, low) -> IRQ 58
Nov 13 12:54:18 localhost kernel: [17179586.492000] cs: IO port probe 0x100-0x3af: clean.
Nov 13 12:54:18 localhost kernel: [17179586.496000] cs: IO port probe 0x3e0-0x4ff: clean.
Nov 13 12:54:18 localhost kernel: [17179586.496000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
Nov 13 12:54:18 localhost kernel: [17179586.496000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
Nov 13 12:54:18 localhost kernel: [17179586.500000] cs: IO port probe 0xa00-0xaff: clean.
Nov 13 12:54:18 localhost kernel: [17179586.964000] Build date: Oct 30 2006
Nov 13 12:54:18 localhost kernel: [17179586.964000] Debugging version (IEEE80211)
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: mac 7.8 phy 4.5 radio 5.6
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 1 for WME_AC_BE traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 0 for WME_AC_BK traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 2 for WME_AC_VI traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 3 for WME_AC_VO traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 8 for CAB traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 9 for beacons
Nov 13 12:54:18 localhost kernel: [17179586.964000] Debugging version (ATH)
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Atheros 5212: mem=0xd0200000, irq=58
Nov 13 12:54:18 localhost kernel: [17179587.680000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Nov 13 12:54:18 localhost kernel: [17179587.816000] lp: driver loaded but no devices found
Nov 13 12:54:18 localhost kernel: [17179587.932000] Adding 650592k swap on /dev/hda5.  Priority:-1 extents:1 across:650592k
Nov 13 12:54:18 localhost kernel: [17179588.156000] EXT3 FS on hda1, internal journal
Nov 13 12:54:18 localhost kernel: [17179588.404000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Nov 13 12:54:18 localhost kernel: [17179588.404000] md: bitmap version 4.39
Nov 13 12:54:18 localhost kernel: [17179589.060000] NET: Registered protocol family 17
Nov 13 12:54:18 localhost kernel: [17179589.364000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Nov 13 12:54:18 localhost kernel: [17179590.700000] cdrom: open failed.
Nov 13 12:54:18 localhost kernel: [17179593.492000] ACPI: AC Adapter [ADP1] (on-line)
Nov 13 12:54:18 localhost kernel: [17179593.664000] ACPI: Battery Slot [BAT0] (battery present)
Nov 13 12:54:18 localhost kernel: [17179593.748000] ACPI: Power Button (FF) [PWRF]
Nov 13 12:54:18 localhost kernel: [17179593.748000] ACPI: Lid Switch [LID0]
Nov 13 12:54:18 localhost kernel: [17179593.748000] ACPI: Sleep Button (CM) [SLPB]
Nov 13 12:54:18 localhost kernel: [17179593.748000] ACPI: Power Button (CM) [PWRB]
Nov 13 12:54:18 localhost kernel: [17179593.844000] ibm_acpi: ec object not found
Nov 13 12:54:18 localhost kernel: [17179593.872000] pcc_acpi: loading...
Nov 13 12:54:18 localhost kernel: [17179593.964000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov 13 12:54:23 localhost hpiod: 0.9.7 accepting connections at 2289... 
Nov 13 12:54:25 localhost kernel: [17179602.620000] NET: Registered protocol family 10
Nov 13 12:54:25 localhost kernel: [17179602.620000] lo: Disabled Privacy Extensions
Nov 13 12:54:25 localhost kernel: [17179602.620000] IPv6 over IPv4 tunneling driver
Nov 13 12:54:25 localhost kernel: [17179602.644000] [drm] Initialized drm 1.0.1 20051102
Nov 13 12:54:25 localhost ntpdate[3439]: step time server 82.211.81.145 offset -0.196407 sec
Nov 13 12:54:28 localhost kernel: [17179605.844000] ppdev: user-space parallel port driver
Nov 13 12:54:29 localhost kernel: [17179606.692000] apm: BIOS not found.
Nov 13 12:54:33 localhost ntpd[4541]: ntpd 4.2.0a@1:4.2.0a+stable-8-r Mon May 29 02:48:41 UTC 2006 (1)
Nov 13 12:54:33 localhost ntpd[4541]: precision = 5.000 usec
Nov 13 12:54:33 localhost ntpd[4541]: Listening on interface wildcard, 0.0.0.0#123
Nov 13 12:54:33 localhost ntpd[4541]: Listening on interface wildcard, ::#123
Nov 13 12:54:33 localhost ntpd[4541]: Listening on interface lo, 127.0.0.1#123
Nov 13 12:54:33 localhost ntpd[4541]: Listening on interface eth0, 207.63.255.11#123
Nov 13 12:54:33 localhost ntpd[4541]: kernel time sync status 0040
Nov 13 12:54:33 localhost ntpd[4541]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Nov 13 12:54:33 localhost hcid[4557]: Bluetooth HCI daemon
Nov 13 12:54:33 localhost kernel: [17179611.008000] Bluetooth: Core ver 2.8
Nov 13 12:54:33 localhost kernel: [17179611.008000] NET: Registered protocol family 31
Nov 13 12:54:33 localhost kernel: [17179611.008000] Bluetooth: HCI device and connection manager initialized
Nov 13 12:54:33 localhost kernel: [17179611.008000] Bluetooth: HCI socket layer initialized
Nov 13 12:54:33 localhost kernel: [17179611.040000] Bluetooth: L2CAP ver 2.8
Nov 13 12:54:33 localhost kernel: [17179611.040000] Bluetooth: L2CAP socket layer initialized
Nov 13 12:54:33 localhost hcid[4557]: Can't get system message bus name: Connection ":1.1" is not allowed to own the service "org.bluez" due to security policies in the configuration file
Nov 13 12:54:33 localhost sdpd[4561]: Bluetooth SDP daemon 
Nov 13 12:54:33 localhost kernel: [17179611.072000] Bluetooth: RFCOMM socket layer initialized
Nov 13 12:54:33 localhost kernel: [17179611.072000] Bluetooth: RFCOMM TTY layer initialized
Nov 13 12:54:33 localhost kernel: [17179611.072000] Bluetooth: RFCOMM ver 1.7
Nov 13 12:54:33 localhost anacron[4609]: Anacron 2.3 started on 2006-11-13
Nov 13 12:54:34 localhost anacron[4609]: Normal exit (0 jobs run)
Nov 13 12:54:34 localhost /usr/sbin/cron[4634]: (CRON) INFO (pidfile fd = 3)
Nov 13 12:54:34 localhost /usr/sbin/cron[4635]: (CRON) STARTUP (fork ok)
Nov 13 12:54:34 localhost /usr/sbin/cron[4635]: (CRON) INFO (Running @reboot jobs)
Nov 13 12:54:36 localhost kernel: [17179613.496000] eth0: no IPv6 routers present
Nov 13 12:55:22 localhost gconfd (john-4811): starting (version 2.14.0), pid 4811 user 'john'
Nov 13 12:55:22 localhost gconfd (john-4811): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov 13 12:55:22 localhost gconfd (john-4811): Resolved address "xml:readwrite:/home/john/.gconf" to a writable configuration source at position 1
Nov 13 12:55:22 localhost gconfd (john-4811): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 13 12:55:22 localhost gconfd (john-4811): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov 13 12:55:22 localhost gconfd (john-4811): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 13 12:55:26 localhost kernel: [17179663.328000] hda-intel: Invalid position buffer, using LPIB read method instead.
Nov 13 12:55:31 localhost gconfd (john-4811): Resolved address "xml:readwrite:/home/john/.gconf" to a writable configuration source at position 0

---

### Post by JPMaximilian on 2006-11-13
xorg log:

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux cbook 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 13 12:55:18 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5a31 card 1025,010b rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 1002,5a36 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 1002,5a38 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 1002,4374 card 1025,010b rev 80 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1025,010b rev 80 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1025,010b rev 80 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 1025,010b rev 83 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 1025,010b rev 80 class 01,01,82 hdr 00
(II) PCI: 00:14:2: chip 1002,437b card 1025,010b rev 01 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 1025,010b rev 80 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 80 class 06,04,01 hdr 81
(II) PCI: 01:05:0: chip 1002,5a62 card 1025,010b rev 00 class 03,00,00 hdr 00
(II) PCI: 0a:00:0: chip 1524,1410 card a400,0000 rev 01 class 06,07,00 hdr 02
(II) PCI: 0a:01:0: chip 10ec,8139 card 1025,0079 rev 10 class 02,00,00 hdr 00
(II) PCI: 0a:06:0: chip 168c,001a card 1468,0418 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,11), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0100000 - 0xd01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:6:0), (0,5,7), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 10: bridge is at (0:20:4), (0,10,14), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 10 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 10 non-prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
(II) Bus 10 prefetchable memory range:
	[0] -1	0	0x10000000 - 0x11ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 11: bridge is at (10:0:0), (10,11,14), BCTRL: 0x05c1 (VGA_EN is cleared)
(II) Bus 11 I/O range:
	[0] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[1] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
(II) Bus 11 prefetchable memory range:
	[0] -1	0	0x10000000 - 0x11ffffff (0x2000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc RC410 [Radeon Xpress 200M] rev 0, Mem @ 0xd4000000/26, 0xd0100000/16, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[1] -1	0	0xd0210000 - 0xd02100ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[3] -1	0	0xd0004400 - 0xd00047ff (0x400) MX[B]
	[4] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[5] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[6] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[7] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[8] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[9] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[10] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[11] -1	0	0x00008480 - 0x00008480 (0x1) IX[B]
	[12] -1	0	0x00008470 - 0x00008470 (0x1) IX[B]
	[13] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[16] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[1] -1	0	0xd0210000 - 0xd02100ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[3] -1	0	0xd0004400 - 0xd00047ff (0x400) MX[B]
	[4] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[5] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[6] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[7] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[8] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[9] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[10] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[11] -1	0	0x00008480 - 0x00008480 (0x1) IX[B]
	[12] -1	0	0x00008470 - 0x00008470 (0x1) IX[B]
	[13] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[16] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[5] -1	0	0xd0210000 - 0xd02100ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[7] -1	0	0xd0004400 - 0xd00047ff (0x400) MX[B]
	[8] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[9] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[10] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[16] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[17] -1	0	0x00008480 - 0x00008480 (0x1) IX[B]
	[18] -1	0	0x00008470 - 0x00008470 (0x1) IX[B]
	[19] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 6.5.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) ATI: ATI driver (version 6.5.8) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:05:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon Xpress 200M (RC410)".
(--) Chipset ATI Radeon XPRESS 200M 5A62 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[5] -1	0	0xd0210000 - 0xd02100ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[7] -1	0	0xd0004400 - 0xd00047ff (0x400) MX[B]
	[8] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[9] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[10] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[16] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[17] -1	0	0x00008480 - 0x00008480 (0x1) IX[B]
	[18] -1	0	0x00008470 - 0x00008470 (0x1) IX[B]
	[19] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 4.0.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[5] -1	0	0xd0210000 - 0xd02100ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[7] -1	0	0xd0004400 - 0xd00047ff (0x400) MX[B]
	[8] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[9] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[10] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[19] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[20] -1	0	0x00008480 - 0x00008480 (0x1) IX[B]
	[21] -1	0	0x00008470 - 0x00008470 (0x1) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[25] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[26] 0	0	0xd01203b0 - 0xd01203bb (0xc) IS[B]
	[27] 0	0	0xd01203c0 - 0xd01203df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xd0100000
(II) RADEON(0): PCI bus 1 card 5 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "UseFBDev" "true"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.0.2
	ABI class: X.Org Video Driver, version 0.8
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(WW) RADEON(0): fbdevHWInit failed, not using framebuffer device
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5A62 (PCIE)" (ChipID = 0x5a62)
(--) RADEON(0): Linear framebuffer at 0xd4000000
(II) RADEON(0): PCI card detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(This repeats a lot)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

---

### Post by JPMaximilian on 2006-11-13
(Continued from previous)

drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card15
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card16
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card17
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card18
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card19
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card20
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card21
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card22
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card23
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card24
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card25
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card26
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card27
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card28
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card29
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card30
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card31
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card32
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card33
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card34
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card35
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card36
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card37
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card38
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card39
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card40
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card41
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card42
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card43
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card44
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card45
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(Repeatins a lot)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card178
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card179
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card180
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card181
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card182
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card183
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card184
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card185
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card186
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card187
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card188
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card189
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card190
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card191
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card192
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card193
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card194
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card195
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card196
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card197
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card198
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card199
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card200
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card201
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card202
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card203
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card204
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card205
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card206
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card207
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card208
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card209
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card210
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card211
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card212
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card213
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card214
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card215
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card216
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card217
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card218
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card219
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card220
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card221
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card222
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card223
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card224
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card225
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card226
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card227
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card228
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card229
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card230
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card231
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card232
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card233
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card234
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card235
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card236
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card237
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card238
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card239
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

drmOpenDevice: node name is /dev/dri/card253
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): Detected total video RAM=7168K, accessible=65536K (PCI BAR=65536K)
(--) RADEON(0): Mapped VideoRAM: 7168 kByte (256 bit DDR SDRAM)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): LVDS port is not in connector table, added in.
(WW) RADEON(0): Unknown DDCType 5 found
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Connector0: DDCType-0, DACType-1, TMDSType--1, ConnectorType-1
(II) RADEON(0): Connector1: DDCType-4, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): DDC Type: 4, Detected Type: 0
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- CRT2_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- Proprietary
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000; xclk=26600
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: QDS                     
(II) RADEON(0): Panel Size from BIOS: 1280x800
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): Valid mode using on-chip RMX: 1280x800
(II) RADEON(0): Total number of valid FP mode(s) found: 1
(--) RADEON(0): Virtual size is 1280x800 (pitch 1280)
(**) RADEON(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   68.90  1280 1296 1328 1408  800 804 808 816
(**) RADEON(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x350"   68.90  640 1296 1328 1408  350 804 808 816
(**) RADEON(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x400"   68.90  640 1296 1328 1408  400 804 808 816
(**) RADEON(0):  Default mode "720x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "720x400"   68.90  720 1296 1328 1408  400 804 808 816
(**) RADEON(0):  Default mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   68.90  640 1296 1328 1408  480 804 808 816
(**) RADEON(0):  Default mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"   68.90  800 1296 1328 1408  600 804 808 816
(**) RADEON(0):  Default mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   68.90  1024 1296 1328 1408  768 804 808 816
(**) RADEON(0):  Default mode "832x624": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "832x624"   68.90  832 1296 1328 1408  624 804 808 816
(**) RADEON(0):  Default mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   68.90  1280 1296 1328 1408  768 804 808 816
(**) RADEON(0):  Default mode "1152x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1152x768"   68.90  1152 1296 1328 1408  768 804 808 816
(++) RADEON(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0100000 - 0xd010ffff (0x10000) MX[B]
	[1] 0	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[7] -1	0	0xd0210000 - 0xd02100ff (0x100) MX[B]
	[8] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[9] -1	0	0xd0004400 - 0xd00047ff (0x400) MX[B]
	[10] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[11] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[12] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[13] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[14] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[22] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[23] -1	0	0x00008480 - 0x00008480 (0x1) IX[B]
	[24] -1	0	0x00008470 - 0x00008470 (0x1) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[28] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[29] 0	0	0xd01203b0 - 0xd01203bb (0xc) IS[B](OprU)
	[30] 0	0	0xd01203c0 - 0xd01203df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit d4000000 0
(**) RADEON(0): Map: 0xd4000000, 0x00700000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81ff058)
(**) RADEON(0): Read: 0x00180006 0x00020073 0x00000000
(**) RADEON(0): Read: rd=6, fd=115, pd=2
(**) RADEON(0): RADEONSaveMode returns 0x81ff058
(II) RADEON(0): Dynamic Clock Scaling Disabled
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x00700000
(**) RADEON(0):   agp_size         : 0x081fef30
(**) RADEON(0):   agp_base         : 0x081fef30
(**) RADEON(0):   MC_FB_LOCATION   : 0x0fff0e00
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1280x800       68.90  1280 1296 1328 1408   800  804  808  816 (24,32)
1280x800       68.90  1280 1296 1328 1408   800  804  808  816 (24,32)
(**) RADEON(0): Pitch = 10485920 bytes (virtualX = 1280, displayWidth = 1280)
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x81ffa08
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ffa08)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x0fff0e00
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 20004c4c to 20127c7c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): Memory manager initialized to (0,0) (1280,1433)
(II) RADEON(0): Reserved area from (0,800) to (1280,802)
(II) RADEON(0): Largest offscreen area available: 1280 x 631
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 160
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		20 128x128 slots
		5 256x256 slots
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 802)
(II) RADEON(0): Largest offscreen area available: 1280 x 627
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
(**) RADEON(0): RADEONSaveScreen(2)
ProcXCloseDevice to close or not ?

---

### Post by JPMaximilian on 2006-11-13
kernel log:
(Some ommitted)
Nov 13 12:50:21 localhost kernel: [17191324.228000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:21 localhost kernel: [17191324.232000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xcab66a80 for 4096000 bytes
Nov 13 12:50:24 localhost kernel: [17191327.128000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2adf000 for 4096000 bytes
Nov 13 12:50:24 localhost kernel: [17191327.152000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:24 localhost kernel: [17191327.156000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc7ddcfc0 for 4096000 bytes
Nov 13 12:50:25 localhost kernel: [17191327.408000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2adf000 for 4096000 bytes
Nov 13 12:50:25 localhost kernel: [17191327.432000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:25 localhost kernel: [17191327.432000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc1433380 for 4096000 bytes
Nov 13 12:50:25 localhost kernel: [17191327.704000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2adf000 for 4096000 bytes
Nov 13 12:50:25 localhost kernel: [17191327.724000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:25 localhost kernel: [17191327.728000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xccc79380 for 4096000 bytes
Nov 13 12:50:26 localhost kernel: [17191328.924000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2adf000 for 4096000 bytes
Nov 13 12:50:26 localhost kernel: [17191328.948000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:26 localhost kernel: [17191328.948000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc13b8180 for 4096000 bytes
Nov 13 12:50:26 localhost kernel: [17191329.136000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2adf000 for 4096000 bytes
Nov 13 12:50:26 localhost kernel: [17191329.156000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:26 localhost kernel: [17191329.156000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc1c7b540 for 4096000 bytes
Nov 13 12:50:27 localhost kernel: [17191329.272000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2adf000 for 4096000 bytes
Nov 13 12:50:27 localhost kernel: [17191329.296000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:27 localhost kernel: [17191329.296000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xcacb7a00 for 4096000 bytes
Nov 13 12:50:27 localhost kernel: [17191329.344000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2a7f000 for 4096000 bytes
Nov 13 12:50:27 localhost kernel: [17191329.368000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:27 localhost kernel: [17191329.368000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xcacb7a40 for 4096000 bytes
Nov 13 12:50:30 localhost kernel: [17191332.736000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2a7f000 for 4096000 bytes
Nov 13 12:50:30 localhost kernel: [17191332.760000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:30 localhost kernel: [17191332.760000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xcddc5580 for 4096000 bytes
Nov 13 12:50:34 localhost kernel: [17191336.412000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2a7f000 for 4096000 bytes
Nov 13 12:50:34 localhost kernel: [17191336.432000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:34 localhost kernel: [17191336.432000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xcacb7c00 for 4096000 bytes
Nov 13 12:50:35 localhost kernel: [17191337.864000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb2a7f000 for 4096000 bytes
Nov 13 12:50:35 localhost kernel: [17191337.888000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Nov 13 12:50:35 localhost kernel: [17191337.888000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc0d86c80 for 4096000 bytes
Nov 13 12:53:22 localhost kernel: [17191504.408000] apm: BIOS not found.
Nov 13 12:53:28 localhost kernel: Kernel logging (proc) stopped.
Nov 13 12:53:28 localhost kernel: Kernel log daemon terminating.
Nov 13 12:54:18 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386
Nov 13 12:54:18 localhost kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Nov 13 12:54:18 localhost kernel: Symbols match kernel version 2.6.15.
Nov 13 12:54:18 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Nov 13 12:54:18 localhost kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
Nov 13 12:54:18 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000000dea0000 (usable)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 000000000dea0000 - 000000000deab000 (ACPI data)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 000000000deab000 - 000000000df00000 (ACPI NVS)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 000000000df00000 - 000000000e000000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Nov 13 12:54:18 localhost kernel: [17179569.184000] 0MB HIGHMEM available.
Nov 13 12:54:18 localhost kernel: [17179569.184000] 222MB LOWMEM available.
Nov 13 12:54:18 localhost kernel: [17179569.184000] found SMP MP-table at 000f8620
Nov 13 12:54:18 localhost kernel: [17179569.184000] On node 0 totalpages: 56992
Nov 13 12:54:18 localhost kernel: [17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
Nov 13 12:54:18 localhost kernel: [17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
Nov 13 12:54:18 localhost kernel: [17179569.184000]   Normal zone: 52896 pages, LIFO batch:15
Nov 13 12:54:18 localhost kernel: [17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
Nov 13 12:54:18 localhost kernel: [17179569.184000] DMI present.
Nov 13 12:54:18 localhost kernel: [17179569.184000] ATI board detected. Disabling timer routing over 8254.
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f85f0
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0dea405e
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: FADT (v001 ATI    Bonefish 0x06040000 ATI  0x000f4240) @ 0x0deaaeb0
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x0deaaf24
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x0deaaf74
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x0deaafc4
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050228) @ 0x0dea45cf
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x0dea409a
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: DSDT (v001    ATI    SB450 0x06040000 MSFT 0x0100000e) @ 0x00000000
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x8008
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: Local APIC address 0xfee00000
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: 2 duplicate APIC table ignored.
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Processor #0 6:14 APIC version 20
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov 13 12:54:18 localhost kernel: [17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Nov 13 12:54:18 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 13 12:54:18 localhost kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Nov 13 12:54:18 localhost kernel: [17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0e000000:f0c00000)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Built 1 zonelists
Nov 13 12:54:18 localhost kernel: [17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
Nov 13 12:54:18 localhost kernel: [17179569.184000] mapped APIC to ffffd000 (fee00000)
Nov 13 12:54:18 localhost kernel: [17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Initializing CPU#0
Nov 13 12:54:18 localhost kernel: [17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
Nov 13 12:54:18 localhost kernel: [17179569.184000] Detected 1463.201 MHz processor.
Nov 13 12:54:18 localhost kernel: [17179569.184000] Using pmtmr for high-res timesource
Nov 13 12:54:18 localhost kernel: [17179569.184000] Console: colour VGA+ 80x25
Nov 13 12:54:18 localhost kernel: [17179570.056000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 13 12:54:18 localhost kernel: [17179570.056000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Nov 13 12:54:18 localhost kernel: [17179570.060000] Memory: 215468k/227968k available (1976k kernel code, 11896k reserved, 606k data, 288k init, 0k highmem)
Nov 13 12:54:18 localhost kernel: [17179570.060000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 13 12:54:18 localhost kernel: [17179570.140000] Calibrating delay using timer specific routine.. 2931.33 BogoMIPS (lpj=5862674)
Nov 13 12:54:18 localhost kernel: [17179570.140000] Security Framework v1.0.0 initialized
Nov 13 12:54:18 localhost kernel: [17179570.140000] SELinux:  Disabled at boot.
Nov 13 12:54:18 localhost kernel: [17179570.140000] Mount-cache hash table entries: 512
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
Nov 13 12:54:18 localhost kernel: [17179570.140000] monitor/mwait feature present.
Nov 13 12:54:18 localhost kernel: [17179570.140000] using mwait in idle threads.
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: L2 cache: 1024K
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 0000c109 00000000 00000000
Nov 13 12:54:18 localhost kernel: [17179570.140000] mtrr: v2.0 (20020519)
Nov 13 12:54:18 localhost kernel: [17179570.140000] CPU: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
Nov 13 12:54:18 localhost kernel: [17179570.140000] Enabling fast FPU save and restore... done.
Nov 13 12:54:18 localhost kernel: [17179570.140000] Enabling unmasked SIMD FPU exception support... done.
Nov 13 12:54:18 localhost kernel: [17179570.140000] Checking 'hlt' instruction... OK.
Nov 13 12:54:18 localhost kernel: [17179570.156000] checking if image is initramfs... it is
Nov 13 12:54:18 localhost kernel: [17179570.888000] Freeing initrd memory: 6617k freed
Nov 13 12:54:18 localhost kernel: [17179570.920000] ACPI: Looking for DSDT ... not found!
Nov 13 12:54:18 localhost kernel: [17179571.332000] ENABLING IO-APIC IRQs
Nov 13 12:54:18 localhost kernel: [17179571.332000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov 13 12:54:18 localhost kernel: [17179571.476000] NET: Registered protocol family 16
Nov 13 12:54:18 localhost kernel: [17179571.476000] EISA bus registered
Nov 13 12:54:18 localhost kernel: [17179571.476000] ACPI: bus type pci registered
Nov 13 12:54:18 localhost kernel: [17179571.476000] PCI: BIOS BUG #81[49435024] found
Nov 13 12:54:18 localhost kernel: [17179571.476000] PCI: Using MMCONFIG
Nov 13 12:54:18 localhost kernel: [17179571.476000] ACPI: Subsystem revision 20051216
Nov 13 12:54:18 localhost kernel: [17179571.480000] ACPI: Interpreter enabled
Nov 13 12:54:18 localhost kernel: [17179571.480000] ACPI: Using IOAPIC for interrupt routing
Nov 13 12:54:18 localhost kernel: [17179571.480000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 13 12:54:18 localhost kernel: [17179571.480000] PCI: Probing PCI hardware (bus 00)
Nov 13 12:54:18 localhost kernel: [17179571.484000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
Nov 13 12:54:18 localhost kernel: [17179571.484000] Boot video device is 0000:01:05.0
Nov 13 12:54:18 localhost kernel: [17179571.484000] PCI: Transparent bridge - 0000:00:14.4
Nov 13 12:54:18 localhost kernel: [17179571.484000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.488000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.488000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.488000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.488000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
Nov 13 12:54:18 localhost kernel: [17179571.492000] ACPI: Embedded Controller [EC0] (gpe 3) interrupt mode.
Nov 13 12:54:18 localhost kernel: [17179571.548000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.548000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Nov 13 12:54:18 localhost kernel: [17179571.552000] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: PnP ACPI init
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: PnP ACPI: found 9 devices
Nov 13 12:54:18 localhost kernel: [17179571.552000] PnPBIOS: Disabled by ACPI PNP
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Using ACPI for IRQ routing
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: 00:05: ioport range 0x1080-0x1080 has been reserved
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: 00:05: ioport range 0x220-0x22f has been reserved
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: 00:05: ioport range 0x40b-0x40b has been reserved
Nov 13 12:54:18 localhost kernel: [17179571.552000] pnp: 00:05: ioport range 0x4d0-0x4d1 has been reserved
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Bridge: 0000:00:01.0
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: 9000-9fff
Nov 13 12:54:18 localhost kernel: [17179571.552000]   MEM window: d0100000-d01fffff
Nov 13 12:54:18 localhost kernel: [17179571.552000]   PREFETCH window: d4000000-d7ffffff
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Bridge: 0000:00:04.0
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000]   MEM window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000]   PREFETCH window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Bridge: 0000:00:06.0
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000]   MEM window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000]   PREFETCH window: disabled.
Nov 13 12:54:18 localhost kernel: [17179571.552000] PCI: Bus 11, cardbus bridge: 0000:0a:00.0
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: 0000a400-0000a4ff
Nov 13 12:54:18 localhost kernel: [17179571.552000]   IO window: 0000a800-0000a8ff
Nov 13 12:54:18 localhost kernel: [17179571.552000]   PREFETCH window: 10000000-11ffffff
Nov 13 12:54:18 localhost kernel: [17179571.556000]   MEM window: 12000000-13ffffff
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Bridge: 0000:00:14.4
Nov 13 12:54:18 localhost kernel: [17179571.556000]   IO window: a000-afff
Nov 13 12:54:18 localhost kernel: [17179571.556000]   MEM window: d0200000-d02fffff
Nov 13 12:54:18 localhost kernel: [17179571.556000]   PREFETCH window: 10000000-11ffffff
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 13 12:54:18 localhost kernel: [17179571.556000] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 22 (level, low) -> IRQ 185
Nov 13 12:54:18 localhost kernel: [17179571.556000] audit: initializing netlink socket (disabled)
Nov 13 12:54:18 localhost kernel: [17179571.556000] audit(1163422435.556:1): initialized
Nov 13 12:54:18 localhost kernel: [17179571.556000] VFS: Disk quotas dquot_6.5.1
Nov 13 12:54:18 localhost kernel: [17179571.556000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 13 12:54:18 localhost kernel: [17179571.556000] Initializing Cryptographic API
Nov 13 12:54:18 localhost kernel: [17179571.556000] io scheduler noop registered
Nov 13 12:54:18 localhost kernel: [17179571.556000] io scheduler anticipatory registered
Nov 13 12:54:18 localhost kernel: [17179571.556000] io scheduler deadline registered
Nov 13 12:54:18 localhost kernel: [17179571.556000] io scheduler cfq registered
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 13 12:54:18 localhost kernel: [17179571.556000] pcie_portdrv_probe->Dev[5a36:1002] has invalid IRQ. Check vendor BIOS
Nov 13 12:54:18 localhost kernel: [17179571.556000] assign_interrupt_mode Found MSI capability
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie00]
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie01]
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie03]
Nov 13 12:54:18 localhost kernel: [17179571.556000] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 13 12:54:18 localhost kernel: [17179571.556000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
Nov 13 12:54:18 localhost kernel: [17179571.556000] assign_interrupt_mode Found MSI capability
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie00]
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie01]
Nov 13 12:54:18 localhost kernel: [17179571.556000] Allocate Port Service[pcie03]
Nov 13 12:54:18 localhost kernel: [17179571.556000] isapnp: Scanning for PnP cards...
Nov 13 12:54:18 localhost kernel: [17179571.912000] isapnp: No Plug & Play device found
Nov 13 12:54:18 localhost kernel: [17179571.928000] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov 13 12:54:18 localhost kernel: [17179571.928000] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 13 12:54:18 localhost kernel: [17179571.928000] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 13 12:54:18 localhost kernel: [17179571.928000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Nov 13 12:54:18 localhost kernel: [17179571.932000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 13 12:54:18 localhost kernel: [17179571.932000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 13 12:54:18 localhost kernel: [17179571.932000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 13 12:54:18 localhost kernel: [17179571.932000] mice: PS/2 mouse device common for all mice
Nov 13 12:54:18 localhost kernel: [17179571.932000] EISA: Probing bus 0 at eisa.0
Nov 13 12:54:18 localhost kernel: [17179571.932000] Cannot allocate resource for EISA slot 1
Nov 13 12:54:18 localhost kernel: [17179571.932000] Cannot allocate resource for EISA slot 8
Nov 13 12:54:18 localhost kernel: [17179571.932000] EISA: Detected 0 cards.
Nov 13 12:54:18 localhost kernel: [17179571.932000] NET: Registered protocol family 2
Nov 13 12:54:18 localhost kernel: [17179571.972000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP: Hash tables configured (established 8192 bind 8192)
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP reno registered
Nov 13 12:54:18 localhost kernel: [17179571.972000] TCP bic registered
Nov 13 12:54:18 localhost kernel: [17179571.972000] NET: Registered protocol family 1
Nov 13 12:54:18 localhost kernel: [17179571.972000] NET: Registered protocol family 8
Nov 13 12:54:18 localhost kernel: [17179571.972000] NET: Registered protocol family 20
Nov 13 12:54:18 localhost kernel: [17179571.972000] Using IPI Shortcut mode
Nov 13 12:54:18 localhost kernel: [17179571.972000] ACPI wakeup devices: 
Nov 13 12:54:18 localhost kernel: [17179571.972000] LID0 SLPB  PB2  PB3  PB4  PB6  PB7 OHC1 OHC2 EHCI  P2P AZLA 
Nov 13 12:54:18 localhost kernel: [17179571.972000] ACPI: (supports S0 S3 S4 S5)
Nov 13 12:54:18 localhost kernel: [17179571.972000] Freeing unused kernel memory: 288k freed
Nov 13 12:54:18 localhost kernel: [17179572.020000] vga16fb: initializing
Nov 13 12:54:18 localhost kernel: [17179572.020000] vga16fb: mapped to 0xc00a0000
Nov 13 12:54:18 localhost kernel: [17179572.112000] Console: switching to colour frame buffer device 80x25
Nov 13 12:54:18 localhost kernel: [17179572.112000] fb0: VGA16 VGA frame buffer device
Nov 13 12:54:18 localhost kernel: [17179572.536000] input: AT Translated Set 2 keyboard as /class/input/input0
Nov 13 12:54:18 localhost kernel: [17179573.232000] Capability LSM initialized
Nov 13 12:54:18 localhost kernel: [17179573.268000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Nov 13 12:54:18 localhost kernel: [17179573.268000] ACPI: Processor [CPU0] (supports 8 throttling states)
Nov 13 12:54:18 localhost kernel: [17179573.324000] ACPI: Thermal Zone [TZS0] (48 C)
Nov 13 12:54:18 localhost kernel: [17179573.380000] ACPI: Thermal Zone [TZS1] (49 C)
Nov 13 12:54:18 localhost kernel: [17179573.828000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
Nov 13 12:54:18 localhost kernel: [17179573.828000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 217
Nov 13 12:54:18 localhost kernel: [17179573.828000] ATIIXP: chipset revision 128
Nov 13 12:54:18 localhost kernel: [17179573.828000] ATIIXP: not 100%% native mode: will probe irqs later
Nov 13 12:54:18 localhost kernel: [17179573.828000]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:DMA, hdb:DMA
Nov 13 12:54:18 localhost kernel: [17179573.828000] ATIIXP: simplex device: DMA disabled
Nov 13 12:54:18 localhost kernel: [17179573.828000] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
Nov 13 12:54:18 localhost kernel: [17179573.828000] Probing IDE interface ide0...
Nov 13 12:54:18 localhost kernel: [17179574.116000] hda: Hitachi IC25N060ATMR04-0, ATA DISK drive
Nov 13 12:54:18 localhost kernel: [17179574.900000] hdb: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, ATAPI CD/DVD-ROM drive
Nov 13 12:54:18 localhost kernel: [17179574.956000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov 13 12:54:18 localhost kernel: [17179574.980000] Probing IDE interface ide1...
Nov 13 12:54:18 localhost kernel: [17179575.548000] hda: max request size: 1024KiB
Nov 13 12:54:18 localhost kernel: [17179575.556000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
Nov 13 12:54:18 localhost kernel: [17179575.556000] hda: cache flushes supported
Nov 13 12:54:18 localhost kernel: [17179575.556000]  hda: hda1 hda2 < hda5 >
Nov 13 12:54:18 localhost kernel: [17179575.608000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Nov 13 12:54:18 localhost kernel: [17179575.608000] Uniform CD-ROM driver Revision: 3.20
Nov 13 12:54:18 localhost kernel: [17179576.052000] usbcore: registered new driver usbfs
Nov 13 12:54:18 localhost kernel: [17179576.052000] usbcore: registered new driver hub
Nov 13 12:54:18 localhost kernel: [17179576.052000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Nov 13 12:54:18 localhost kernel: [17179576.052000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 225
Nov 13 12:54:18 localhost kernel: [17179576.052000] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 13 12:54:18 localhost kernel: [17179576.056000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Nov 13 12:54:18 localhost kernel: [17179576.056000] ohci_hcd 0000:00:13.0: irq 225, io mem 0xd0005000
Nov 13 12:54:18 localhost kernel: [17179576.064000] hub 1-0:1.0: USB hub found
Nov 13 12:54:18 localhost kernel: [17179576.064000] hub 1-0:1.0: 4 ports detected
Nov 13 12:54:18 localhost kernel: [17179576.168000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 225
Nov 13 12:54:18 localhost kernel: [17179576.168000] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 13 12:54:18 localhost kernel: [17179576.168000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Nov 13 12:54:18 localhost kernel: [17179576.168000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xd0006000
Nov 13 12:54:18 localhost kernel: [17179576.172000] hub 2-0:1.0: USB hub found
Nov 13 12:54:18 localhost kernel: [17179576.172000] hub 2-0:1.0: 4 ports detected
Nov 13 12:54:18 localhost kernel: [17179576.276000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 225
Nov 13 12:54:18 localhost kernel: [17179576.276000] ehci_hcd 0000:00:13.2: EHCI Host Controller
Nov 13 12:54:18 localhost kernel: [17179576.276000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Nov 13 12:54:18 localhost kernel: [17179576.276000] ehci_hcd 0000:00:13.2: irq 225, io mem 0xd0007000
Nov 13 12:54:18 localhost kernel: [17179576.276000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 13 12:54:18 localhost kernel: [17179576.276000] hub 3-0:1.0: USB hub found
Nov 13 12:54:18 localhost kernel: [17179576.276000] hub 3-0:1.0: 8 ports detected
Nov 13 12:54:18 localhost kernel: [17179576.392000] Probing IDE interface ide1...
Nov 13 12:54:18 localhost kernel: [17179576.868000] usb 1-1: new low speed USB device using ohci_hcd and address 3
Nov 13 12:54:18 localhost kernel: [17179577.056000] Attempting manual resume
Nov 13 12:54:18 localhost kernel: [17179577.088000] usbcore: registered new driver hiddev
Nov 13 12:54:18 localhost kernel: [17179577.096000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
Nov 13 12:54:18 localhost kernel: [17179577.096000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1
Nov 13 12:54:18 localhost kernel: [17179577.096000] usbcore: registered new driver usbhid
Nov 13 12:54:18 localhost kernel: [17179577.096000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Nov 13 12:54:18 localhost kernel: [17179577.144000] EXT3-fs: mounted filesystem with ordered data mode.
Nov 13 12:54:18 localhost kernel: [17179577.156000] kjournald starting.  Commit interval 5 seconds
Nov 13 12:54:18 localhost kernel: [17179583.232000] ts: Compaq touchscreen protocol output
Nov 13 12:54:18 localhost kernel: [17179584.612000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 13 12:54:18 localhost kernel: [17179584.616000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 13 12:54:18 localhost kernel: [17179584.948000] Linux agpgart interface v0.101 (c) Dave Jones
Nov 13 12:54:18 localhost kernel: [17179585.344000] Real Time Clock Driver v1.12
Nov 13 12:54:18 localhost kernel: [17179585.380000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 217
Nov 13 12:54:18 localhost kernel: [17179585.492000] input: PC Speaker as /class/input/input2
Nov 13 12:54:18 localhost kernel: [17179585.872000] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 22 (level, low) -> IRQ 185
Nov 13 12:54:18 localhost kernel: [17179585.872000] Yenta: CardBus bridge found at 0000:0a:00.0 [1025:0080]
Nov 13 12:54:18 localhost kernel: [17179585.872000] Yenta: Using CSCINT to route CSC interrupts to PCI
Nov 13 12:54:18 localhost kernel: [17179585.872000] Yenta: Routing CardBus interrupts to PCI
Nov 13 12:54:18 localhost kernel: [17179585.872000] Yenta TI: socket 0000:0a:00.0, mfunc 0x01aa1b22, devctl 0x44
Nov 13 12:54:18 localhost kernel: [17179585.928000] 8139too Fast Ethernet driver 0.9.27
Nov 13 12:54:18 localhost kernel: [17179586.044000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x204000
Nov 13 12:54:18 localhost kernel: [17179586.068000] ath_hal: module license 'Proprietary' taints kernel.
Nov 13 12:54:18 localhost kernel: [17179586.068000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
Nov 13 12:54:18 localhost kernel: [17179586.076000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Nov 13 12:54:18 localhost kernel: [17179586.080000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Nov 13 12:54:18 localhost kernel: [17179586.104000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
Nov 13 12:54:18 localhost kernel: [17179586.104000] Socket status: 30000006
Nov 13 12:54:18 localhost kernel: [17179586.104000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0c to #0e
Nov 13 12:54:18 localhost kernel: [17179586.104000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
Nov 13 12:54:18 localhost kernel: [17179586.104000] cs: IO port probe 0xa000-0xafff: clean.
Nov 13 12:54:18 localhost kernel: [17179586.104000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
Nov 13 12:54:18 localhost kernel: [17179586.104000] pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x11ffffff
Nov 13 12:54:18 localhost kernel: [17179586.120000] ACPI: PCI Interrupt 0000:0a:01.0[A] -> GSI 20 (level, low) -> IRQ 50
Nov 13 12:54:18 localhost kernel: [17179586.120000] eth0: RealTek RTL8139 at 0xce9bc000, 00:16:d3:42:8a:f5, IRQ 50
Nov 13 12:54:18 localhost kernel: [17179586.120000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Nov 13 12:54:18 localhost kernel: [17179586.140000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Nov 13 12:54:18 localhost kernel: [17179586.204000] wlan: 0.8.6.0 (EXPERIMENTAL)
Nov 13 12:54:18 localhost kernel: [17179586.208000] ath_rate_sample: 1.2
Nov 13 12:54:18 localhost kernel: [17179586.228000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
Nov 13 12:54:18 localhost kernel: [17179586.228000] ACPI: PCI Interrupt 0000:0a:06.0[A] -> GSI 23 (level, low) -> IRQ 58
Nov 13 12:54:18 localhost kernel: [17179586.492000] cs: IO port probe 0x100-0x3af: clean.
Nov 13 12:54:18 localhost kernel: [17179586.496000] cs: IO port probe 0x3e0-0x4ff: clean.
Nov 13 12:54:18 localhost kernel: [17179586.496000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
Nov 13 12:54:18 localhost kernel: [17179586.496000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
Nov 13 12:54:18 localhost kernel: [17179586.500000] cs: IO port probe 0xa00-0xaff: clean.
Nov 13 12:54:18 localhost kernel: [17179586.964000] Build date: Oct 30 2006
Nov 13 12:54:18 localhost kernel: [17179586.964000] Debugging version (IEEE80211)
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: mac 7.8 phy 4.5 radio 5.6
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 1 for WME_AC_BE traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 0 for WME_AC_BK traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 2 for WME_AC_VI traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 3 for WME_AC_VO traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 8 for CAB traffic
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Use hw queue 9 for beacons
Nov 13 12:54:18 localhost kernel: [17179586.964000] Debugging version (ATH)
Nov 13 12:54:18 localhost kernel: [17179586.964000] ath0: Atheros 5212: mem=0xd0200000, irq=58
Nov 13 12:54:18 localhost kernel: [17179587.680000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Nov 13 12:54:18 localhost kernel: [17179587.816000] lp: driver loaded but no devices found
Nov 13 12:54:18 localhost kernel: [17179587.932000] Adding 650592k swap on /dev/hda5.  Priority:-1 extents:1 across:650592k
Nov 13 12:54:18 localhost kernel: [17179588.156000] EXT3 FS on hda1, internal journal
Nov 13 12:54:18 localhost kernel: [17179588.404000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Nov 13 12:54:18 localhost kernel: [17179588.404000] md: bitmap version 4.39
Nov 13 12:54:18 localhost kernel: [17179589.060000] NET: Registered protocol family 17
Nov 13 12:54:18 localhost kernel: [17179589.364000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Nov 13 12:54:18 localhost kernel: [17179590.700000] cdrom: open failed.
Nov 13 12:54:18 localhost kernel: [17179593.492000] ACPI: AC Adapter [ADP1] (on-line)
Nov 13 12:54:18 localhost kernel: [17179593.664000] ACPI: Battery Slot [BAT0] (battery present)
Nov 13 12:54:18 localhost kernel: [17179593.748000] ACPI: Power Button (FF) [PWRF]
Nov 13 12:54:18 localhost kernel: [17179593.748000] ACPI: Lid Switch [LID0]
Nov 13 12:54:18 localhost kernel: [17179593.748000] ACPI: Sleep Button (CM) [SLPB]
Nov 13 12:54:18 localhost kernel: [17179593.748000] ACPI: Power Button (CM) [PWRB]
Nov 13 12:54:18 localhost kernel: [17179593.844000] ibm_acpi: ec object not found
Nov 13 12:54:18 localhost kernel: [17179593.872000] pcc_acpi: loading...
Nov 13 12:54:18 localhost kernel: [17179593.964000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov 13 12:54:25 localhost kernel: [17179602.620000] NET: Registered protocol family 10
Nov 13 12:54:25 localhost kernel: [17179602.620000] lo: Disabled Privacy Extensions
Nov 13 12:54:25 localhost kernel: [17179602.620000] IPv6 over IPv4 tunneling driver
Nov 13 12:54:25 localhost kernel: [17179602.644000] [drm] Initialized drm 1.0.1 20051102
Nov 13 12:54:28 localhost kernel: [17179605.844000] ppdev: user-space parallel port driver
Nov 13 12:54:29 localhost kernel: [17179606.692000] apm: BIOS not found.
Nov 13 12:54:33 localhost kernel: [17179611.008000] Bluetooth: Core ver 2.8
Nov 13 12:54:33 localhost kernel: [17179611.008000] NET: Registered protocol family 31
Nov 13 12:54:33 localhost kernel: [17179611.008000] Bluetooth: HCI device and connection manager initialized
Nov 13 12:54:33 localhost kernel: [17179611.008000] Bluetooth: HCI socket layer initialized
Nov 13 12:54:33 localhost kernel: [17179611.040000] Bluetooth: L2CAP ver 2.8
Nov 13 12:54:33 localhost kernel: [17179611.040000] Bluetooth: L2CAP socket layer initialized
Nov 13 12:54:33 localhost kernel: [17179611.072000] Bluetooth: RFCOMM socket layer initialized
Nov 13 12:54:33 localhost kernel: [17179611.072000] Bluetooth: RFCOMM TTY layer initialized
Nov 13 12:54:33 localhost kernel: [17179611.072000] Bluetooth: RFCOMM ver 1.7
Nov 13 12:54:36 localhost kernel: [17179613.496000] eth0: no IPv6 routers present
Nov 13 12:55:26 localhost kernel: [17179663.328000] hda-intel: Invalid position buffer, using LPIB read method instead.

---

### Post by StormGuy on 2006-11-13
I broke my X Sever once too (just a few days ago) :)

See if this helps:

[http://ubuntuforums.org/showthread.php?t=292599](http://ubuntuforums.org/showthread.php?t=292599)

---

