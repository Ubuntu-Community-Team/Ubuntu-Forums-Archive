---
title: "system hangs"
date: 2007-01-28
forum: General Help
---

### Post by ffpcs on 2007-01-28
As a newbie, I am asking forgiveness ahead of time and welcome any guidance on the proper method of presenting requests for help.  Having said that, I included the partial contents of my syslog here because I am unsure if I was able to successfully ATTACH it. I included the log from up to the freeze through the first successful GRAHPICAL boot after it (there was an intervening "character" boot. I apologize if I am not using the correct terminology.

In any event, If left idle for a few hours, the system will become totally unresponsive to the point of requiring a reboot.  As you can see from the log, it hapened at the entry - Jan 27 19:55:46 in the log.  Is there a way to tell from the information contained in the log PRIOR to the freeze, what might have caused it?  Any help would be appreciated. I included as much of the log as I could and still post this. If the attachment was successful, there is more information in the log.

Thank you. -Frank

Jan 27 07:55:26 millennia -- MARK --
Jan 27 08:15:26 millennia -- MARK --
Jan 27 08:17:01 millennia /USR/SBIN/CRON[23930]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 08:35:26 millennia -- MARK --
Jan 27 08:55:26 millennia -- MARK --
Jan 27 09:15:27 millennia -- MARK --
Jan 27 09:17:01 millennia /USR/SBIN/CRON[25370]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 09:35:27 millennia -- MARK --
Jan 27 09:55:27 millennia -- MARK --
Jan 27 10:08:21 millennia gconfd (frank-26607): starting (version 2.14.0), pid 26607 user 'frank'
Jan 27 10:08:21 millennia gconfd (frank-26607): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 27 10:08:21 millennia gconfd (frank-26607): Resolved address "xml:readwrite:/home/frank/.gconf" to a writable configuration source at position 1
Jan 27 10:08:21 millennia gconfd (frank-26607): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 27 10:08:21 millennia gconfd (frank-26607): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 27 10:08:21 millennia gconfd (frank-26607): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 27 10:08:42 millennia gconfd (frank-26607): Resolved address "xml:readwrite:/home/frank/.gconf" to a writable configuration source at position 0
Jan 27 10:17:01 millennia /USR/SBIN/CRON[26972]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 10:35:30 millennia -- MARK --
Jan 27 10:55:32 millennia -- MARK --
Jan 27 11:15:33 millennia -- MARK --
Jan 27 11:17:01 millennia /USR/SBIN/CRON[28316]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 11:35:33 millennia -- MARK --
Jan 27 11:55:33 millennia -- MARK --
Jan 27 12:15:34 millennia -- MARK --
Jan 27 12:17:01 millennia /USR/SBIN/CRON[29756]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 12:35:34 millennia -- MARK --
Jan 27 12:55:34 millennia -- MARK --
Jan 27 13:15:34 millennia -- MARK --
Jan 27 13:17:01 millennia /USR/SBIN/CRON[31198]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 13:35:35 millennia -- MARK --
Jan 27 13:55:35 millennia -- MARK --
Jan 27 14:15:35 millennia -- MARK --
Jan 27 14:17:01 millennia /USR/SBIN/CRON[32638]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 14:35:35 millennia -- MARK --
Jan 27 14:55:36 millennia -- MARK --
Jan 27 15:15:36 millennia -- MARK --
Jan 27 15:17:01 millennia /USR/SBIN/CRON[1613]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 15:35:36 millennia -- MARK --
Jan 27 15:55:36 millennia -- MARK --
Jan 27 16:15:36 millennia -- MARK --
Jan 27 16:17:01 millennia /USR/SBIN/CRON[3058]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 16:35:37 millennia -- MARK --
Jan 27 16:49:23 millennia dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 27 16:49:23 millennia dhclient: DHCPACK from 192.168.1.1
Jan 27 16:49:23 millennia dhclient: bound to 192.168.1.169 -- renewal in 40066 seconds.
Jan 27 17:15:37 millennia -- MARK --
Jan 27 17:17:01 millennia /USR/SBIN/CRON[4533]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 17:35:37 millennia -- MARK --
Jan 27 17:55:38 millennia -- MARK --
Jan 27 18:15:38 millennia -- MARK --
Jan 27 18:17:01 millennia /USR/SBIN/CRON[5992]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 18:35:40 millennia -- MARK --
Jan 27 18:39:49 millennia gconfd (frank-26607): Received signal 11, dumping core. Please report a GConf bug.
Jan 27 18:39:50 millennia gconfd (frank-6500): starting (version 2.14.0), pid 6500 user 'frank'
Jan 27 18:39:50 millennia gconfd (frank-6500): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 27 18:39:51 millennia gconfd (frank-6500): Resolved address "xml:readwrite:/home/frank/.gconf" to a writable configuration source at position 1
Jan 27 18:39:51 millennia gconfd (frank-6500): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 27 18:39:51 millennia gconfd (frank-6500): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 27 18:39:51 millennia gconfd (frank-6500): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 27 18:41:21 millennia gdm[4245]: Error reinitilizing server
Jan 27 18:54:25 millennia gconfd (frank-6500): Resolved address "xml:readwrite:/home/frank/.gconf" to a writable configuration source at position 0
Jan 27 19:15:41 millennia -- MARK --
Jan 27 19:17:01 millennia /USR/SBIN/CRON[7263]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 27 19:35:41 millennia -- MARK --
Jan 27 19:55:46 millennia -- MARK --
Jan 28 08:47:39 millennia syslogd 1.4.1#17ubuntu7: restart.
Jan 28 08:47:39 millennia kernel: Inspecting /boot/System.map-2.6.15-27-386
Jan 28 08:47:39 millennia kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Jan 28 08:47:39 millennia kernel: Symbols match kernel version 2.6.15.
Jan 28 08:47:39 millennia kernel: No module symbols loaded - kernel modules not enabled. 
Jan 28 08:47:39 millennia kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006
Jan 28 08:47:39 millennia kernel: [17179569.184000] BIOS-provided physical RAM map:
Jan 28 08:47:39 millennia kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan 28 08:47:39 millennia kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan 28 08:47:39 millennia kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 28 08:47:39 millennia kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
Jan 28 08:47:39 millennia kernel: [17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
Jan 28 08:47:39 millennia kernel: [17179569.184000]  BIOS-e820: 000000000fff3000 - 0000000010000000 (ACPI data)
Jan 28 08:47:39 millennia kernel: [17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Jan 28 08:47:39 millennia kernel: [17179569.184000] 0MB HIGHMEM available.
Jan 28 08:47:39 millennia kernel: [17179569.184000] 255MB LOWMEM available.
Jan 28 08:47:39 millennia kernel: [17179569.184000] On node 0 totalpages: 65520
Jan 28 08:47:39 millennia kernel: [17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
Jan 28 08:47:39 millennia kernel: [17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
Jan 28 08:47:39 millennia kernel: [17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
Jan 28 08:47:39 millennia kernel: [17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
Jan 28 08:47:39 millennia kernel: [17179569.184000] DMI 2.3 present.
Jan 28 08:47:39 millennia kernel: [17179569.184000] ACPI: RSDP (v000 VIA694                                ) @ 0x000f6a50
Jan 28 08:47:39 millennia kernel: [17179569.184000] ACPI: RSDT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3000
Jan 28 08:47:39 millennia kernel: [17179569.184000] ACPI: FADT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3040
Jan 28 08:47:39 millennia kernel: [17179569.184000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
Jan 28 08:47:39 millennia kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x4008
Jan 28 08:47:39 millennia kernel: [17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
Jan 28 08:47:39 millennia kernel: [17179569.184000] Built 1 zonelists
Jan 28 08:47:39 millennia kernel: [17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
Jan 28 08:47:39 millennia kernel: [17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
Jan 28 08:47:39 millennia kernel: [17179569.184000] mapped APIC to ffffd000 (01201000)
Jan 28 08:47:39 millennia kernel: [17179569.184000] Initializing CPU#0
Jan 28 08:47:39 millennia kernel: [17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
Jan 28 08:47:39 millennia kernel: [17179569.184000] Detected 799.888 MHz processor.
Jan 28 08:47:39 millennia kernel: [17179569.184000] Using pmtmr for high-res timesource
Jan 28 08:47:39 millennia kernel: [17179569.184000] Console: colour VGA+ 80x25
Jan 28 08:47:39 millennia kernel: [17179571.572000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 28 08:47:39 millennia kernel: [17179571.576000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 28 08:47:39 millennia kernel: [17179571.596000] Memory: 249140k/262080k available (1976k kernel code, 12356k reserved, 606k data, 288k init, 0k highmem)
Jan 28 08:47:39 millennia kernel: [17179571.596000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jan 28 08:47:39 millennia kernel: [17179571.676000] Calibrating delay using timer specific routine.. 1601.19 BogoMIPS (lpj=3202383)
Jan 28 08:47:39 millennia kernel: [17179571.676000] Security Framework v1.0.0 initialized
Jan 28 08:47:39 millennia kernel: [17179571.676000] SELinux:  Disabled at boot.
Jan 28 08:47:39 millennia kernel: [17179571.676000] Mount-cache hash table entries: 512
Jan 28 08:47:39 millennia kernel: [17179571.676000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
Jan 28 08:47:39 millennia kernel: [17179571.676000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
Jan 28 08:47:39 millennia kernel: [17179571.676000] CPU: L1 I cache: 16K, L1 D cache: 16K
Jan 28 08:47:39 millennia kernel: [17179571.676000] CPU: L2 cache: 256K
Jan 28 08:47:39 millennia kernel: [17179571.676000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
Jan 28 08:47:39 millennia kernel: [17179571.676000] mtrr: v2.0 (20020519)
Jan 28 08:47:39 millennia kernel: [17179571.676000] CPU: Intel Pentium III (Coppermine) stepping 01
Jan 28 08:47:39 millennia kernel: [17179571.676000] Enabling fast FPU save and restore... done.
Jan 28 08:47:39 millennia kernel: [17179571.676000] Enabling unmasked SIMD FPU exception support... done.
Jan 28 08:47:39 millennia kernel: [17179571.676000] Checking 'hlt' instruction... OK.
Jan 28 08:47:39 millennia kernel: [17179571.692000] checking if image is initramfs... it is
Jan 28 08:47:39 millennia kernel: [17179573.584000] Freeing initrd memory: 6616k freed
Jan 28 08:47:39 millennia kernel: [17179573.612000] ACPI: Looking for DSDT ... not found!
Jan 28 08:47:39 millennia kernel: [17179573.612000] ACPI: setting ELCR to 0200 (from 0e20)
Jan 28 08:47:39 millennia kernel: [17179573.616000] NET: Registered protocol family 16
Jan 28 08:47:39 millennia kernel: [17179573.616000] EISA bus registered
Jan 28 08:47:39 millennia kernel: [17179573.616000] ACPI: bus type pci registered
Jan 28 08:47:39 millennia kernel: [17179573.632000] PCI: PCI BIOS revision 2.10 entry at 0xfb290, last bus=1
Jan 28 08:47:39 millennia kernel: [17179573.632000] PCI: Using configuration type 1
Jan 28 08:47:39 millennia kernel: [17179573.632000] ACPI: Subsystem revision 20051216
Jan 28 08:47:39 millennia kernel: [17179573.640000] ACPI: Interpreter enabled
Jan 28 08:47:39 millennia kernel: [17179573.640000] ACPI: Using PIC for interrupt routing
Jan 28 08:47:39 millennia kernel: [17179573.644000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 28 08:47:39 millennia kernel: [17179573.644000] PCI: Probing PCI hardware (bus 00)
Jan 28 08:47:39 millennia kernel: [17179573.644000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Jan 28 08:47:39 millennia kernel: [17179573.648000] Boot video device is 0000:01:00.0
Jan 28 08:47:39 millennia kernel: [17179573.648000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 28 08:47:39 millennia kernel: [17179573.652000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Jan 28 08:47:39 millennia kernel: [17179573.652000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
Jan 28 08:47:39 millennia kernel: [17179573.652000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *9
Jan 28 08:47:39 millennia kernel: [17179573.652000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
Jan 28 08:47:39 millennia kernel: [17179573.656000] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 28 08:47:39 millennia kernel: [17179573.656000] pnp: PnP ACPI init
Jan 28 08:47:39 millennia kernel: [17179573.664000] pnp: PnP ACPI: found 12 devices
Jan 28 08:47:39 millennia kernel: [17179573.664000] PnPBIOS: Disabled by ACPI PNP
Jan 28 08:47:39 millennia kernel: [17179573.664000] PCI: Using ACPI for IRQ routing
Jan 28 08:47:39 millennia kernel: [17179573.664000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jan 28 08:47:39 millennia kernel: [17179573.668000] PCI: Bridge: 0000:00:01.0
Jan 28 08:47:39 millennia kernel: [17179573.668000]   IO window: disabled.
Jan 28 08:47:39 millennia kernel: [17179573.668000]   MEM window: d8000000-d9ffffff
Jan 28 08:47:39 millennia kernel: [17179573.668000]   PREFETCH window: da000000-dbffffff
Jan 28 08:47:39 millennia kernel: [17179573.668000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Jan 28 08:47:39 millennia kernel: [17179573.668000] audit: initializing netlink socket (disabled)
Jan 28 08:47:39 millennia kernel: [17179573.668000] audit(1169992026.668:1): initialized
Jan 28 08:47:39 millennia kernel: [17179573.668000] VFS: Disk quotas dquot_6.5.1
Jan 28 08:47:39 millennia kernel: [17179573.668000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 28 08:47:39 millennia kernel: [17179573.668000] Initializing Cryptographic API
Jan 28 08:47:39 millennia kernel: [17179573.668000] io scheduler noop registered
Jan 28 08:47:39 millennia kernel: [17179573.668000] io scheduler anticipatory registered
Jan 28 08:47:39 millennia kernel: [17179573.668000] io scheduler deadline registered
Jan 28 08:47:39 millennia kernel: [17179573.668000] io scheduler cfq registered
Jan 28 08:47:39 millennia kernel: [17179573.668000] Activating ISA DMA hang workarounds.
Jan 28 08:47:39 millennia kernel: [17179573.668000] isapnp: Scanning for PnP cards...
Jan 28 08:47:39 millennia kernel: [17179574.024000] isapnp: No Plug & Play device found
Jan 28 08:47:39 millennia kernel: [17179574.060000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 28 08:47:39 millennia kernel: [17179574.076000] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 28 08:47:39 millennia kernel: [17179574.076000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 28 08:47:39 millennia kernel: [17179574.076000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Jan 28 08:47:39 millennia kernel: [17179574.076000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 28 08:47:39 millennia kernel: [17179574.076000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jan 28 08:47:39 millennia kernel: [17179574.084000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 28 08:47:39 millennia kernel: [17179574.084000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jan 28 08:47:39 millennia kernel: [17179574.084000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jan 28 08:47:39 millennia kernel: [17179574.084000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jan 28 08:47:39 millennia kernel: [17179574.084000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jan 28 08:47:39 millennia kernel: [17179574.084000] mice: PS/2 mouse device common for all mice
Jan 28 08:47:39 millennia kernel: [17179574.088000] EISA: Probing bus 0 at eisa.0
Jan 28 08:47:39 millennia kernel: [17179574.088000] Cannot allocate resource for EISA slot 4
Jan 28 08:47:39 millennia kernel: [17179574.088000] EISA: Detected 0 cards.
Jan 28 08:47:39 millennia kernel: [17179574.088000] NET: Registered protocol family 2
Jan 28 08:47:39 millennia kernel: [17179574.128000] input: AT Translated Set 2 keyboard as /class/input/input0
Jan 28 08:47:39 millennia kernel: [17179574.140000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jan 28 08:47:39 millennia kernel: [17179574.140000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
Jan 28 08:47:39 millennia kernel: [17179574.140000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
Jan 28 08:47:39 millennia kernel: [17179574.140000] TCP: Hash tables configured (established 16384 bind 16384)
Jan 28 08:47:39 millennia kernel: [17179574.140000] TCP reno registered
Jan 28 08:47:39 millennia kernel: [17179574.140000] TCP bic registered
Jan 28 08:47:39 millennia kernel: [17179574.140000] NET: Registered protocol family 1
Jan 28 08:47:39 millennia kernel: [17179574.140000] NET: Registered protocol family 8
Jan 28 08:47:39 millennia kernel: [17179574.140000] NET: Registered protocol family 20
Jan 28 08:47:39 millennia kernel: [17179574.140000] Using IPI Shortcut mode
Jan 28 08:47:39 millennia kernel: [17179574.140000] ACPI wakeup devices: 
Jan 28 08:47:39 millennia kernel: [17179574.140000] PWRB PCI0 USB0 
Jan 28 08:47:39 millennia kernel: [17179574.140000] ACPI: (supports S0 S1 S5)
Jan 28 08:47:39 millennia kernel: [17179574.140000] Freeing unused kernel memory: 288k freed
Jan 28 08:47:39 millennia kernel: [17179574.260000] vga16fb: initializing
Jan 28 08:47:39 millennia kernel: [17179574.260000] vga16fb: mapped to 0xc00a0000
Jan 28 08:47:39 millennia kernel: [17179574.372000] Console: switching to colour frame buffer device 80x25
Jan 28 08:47:39 millennia kernel: [17179574.372000] fb0: VGA16 VGA frame buffer device
Jan 28 08:47:39 millennia kernel: [17179575.492000] Capability LSM initialized
Jan 28 08:47:39 millennia kernel: [17179575.572000] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jan 28 08:47:39 millennia kernel: [17179575.572000] ACPI: Processor [CPU0] (supports 2 throttling states)
Jan 28 08:47:39 millennia kernel: [17179576.696000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
Jan 28 08:47:39 millennia kernel: [17179576.696000] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
Jan 28 08:47:39 millennia kernel: [17179576.696000] VP_IDE: chipset revision 6
Jan 28 08:47:39 millennia kernel: [17179576.696000] VP_IDE: not 100%% native mode: will probe irqs later
Jan 28 08:47:39 millennia kernel: [17179576.696000] VP_IDE: VIA vt82c596b (rev 12) IDE UDMA66 controller on pci0000:00:07.1
Jan 28 08:47:39 millennia kernel: [17179576.696000]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
Jan 28 08:47:39 millennia kernel: [17179576.696000]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:pio
Jan 28 08:47:39 millennia kernel: [17179576.696000] Probing IDE interface ide0...
Jan 28 08:47:39 millennia kernel: [17179577.116000] hda: MAXTOR 6L080J4, ATA DISK drive
Jan 28 08:47:39 millennia kernel: [17179577.116000] hda: IRQ probe failed (0xfffffdf8)
Jan 28 08:47:39 millennia kernel: [17179577.916000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jan 28 08:47:39 millennia kernel: [17179577.916000] Probing IDE interface ide1...
Jan 28 08:47:39 millennia kernel: [17179578.780000] hdc: SONY CD-RW CRX230E, ATAPI CD/DVD-ROM drive
Jan 28 08:47:39 millennia kernel: [17179579.452000] ide1 at 0x170-0x177,0x376 on irq 15
Jan 28 08:47:39 millennia kernel: [17179579.464000] hda: max request size: 128KiB
Jan 28 08:47:39 millennia kernel: [17179579.484000] hda: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(66)
Jan 28 08:47:39 millennia kernel: [17179579.488000] hda: cache flushes supported
Jan 28 08:47:39 millennia kernel: [17179579.488000]  hda: hda1 hda2 < hda5 >
Jan 28 08:47:39 millennia kernel: [17179579.516000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Jan 28 08:47:39 millennia kernel: [17179579.516000] Uniform CD-ROM driver Revision: 3.20
Jan 28 08:47:39 millennia kernel: [17179579.836000] usbcore: registered new driver usbfs
Jan 28 08:47:39 millennia kernel: [17179579.836000] usbcore: registered new driver hub
Jan 28 08:47:39 millennia kernel: [17179579.844000] USB Universal Host Controller Interface driver v2.3
Jan 28 08:47:39 millennia kernel: [17179579.844000] **** SET: Misaligned resource pointer: cfd295e2 Type 07 Len 0
Jan 28 08:47:39 millennia kernel: [17179579.844000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
Jan 28 08:47:39 millennia kernel: [17179579.844000] PCI: setting IRQ 10 as level-triggered
Jan 28 08:47:39 millennia kernel: [17179579.844000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Jan 28 08:47:39 millennia kernel: [17179579.844000] uhci_hcd 0000:00:07.2: UHCI Host Controller
Jan 28 08:47:39 millennia kernel: [17179579.844000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Jan 28 08:47:39 millennia kernel: [17179579.844000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000d400
Jan 28 08:47:39 millennia kernel: [17179579.844000] hub 1-0:1.0: USB hub found
Jan 28 08:47:39 millennia kernel: [17179579.844000] hub 1-0:1.0: 2 ports detected
Jan 28 08:47:39 millennia kernel: [17179580.048000] Attempting manual resume
Jan 28 08:47:39 millennia kernel: [17179580.072000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jan 28 08:47:39 millennia kernel: [17179580.072000] EXT3-fs: write access will be enabled during recovery.
Jan 28 08:47:39 millennia kernel: [17179582.868000] EXT3-fs: recovery complete.
Jan 28 08:47:39 millennia kernel: [17179582.868000] kjournald starting.  Commit interval 5 seconds
Jan 28 08:47:39 millennia kernel: [17179582.876000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 28 08:47:39 millennia kernel: [17179593.484000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 28 08:47:39 millennia kernel: [17179593.504000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 28 08:47:39 millennia kernel: [17179593.628000] **** SET: Misaligned resource pointer: cfcd9202 Type 07 Len 0
Jan 28 08:47:39 millennia kernel: [17179593.628000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Jan 28 08:47:39 millennia kernel: [17179593.628000] PCI: setting IRQ 5 as level-triggered
Jan 28 08:47:39 millennia kernel: [17179593.628000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Jan 28 08:47:39 millennia kernel: [17179593.628000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
Jan 28 08:47:39 millennia kernel: [17179593.628000] 0000:00:0f.0: 3Com PCI 3c905C Tornado at d0886000. Vers LK1.1.19
Jan 28 08:47:39 millennia kernel: [17179594.708000] Real Time Clock Driver v1.12
Jan 28 08:47:39 millennia kernel: [17179595.156000] Floppy drive(s): fd0 is 1.44M
Jan 28 08:47:39 millennia kernel: [17179595.168000] Linux agpgart interface v0.101 (c) Dave Jones
Jan 28 08:47:39 millennia kernel: [17179595.176000] FDC 0 is a post-1991 82077
Jan 28 08:47:39 millennia kernel: [17179595.184000] agpgart: Detected VIA Apollo Pro 133 chipset
Jan 28 08:47:39 millennia kernel: [17179595.192000] agpgart: AGP aperture is 128M @ 0xd0000000
Jan 28 08:47:39 millennia kernel: [17179595.228000] parport: PnPBIOS parport detected.
Jan 28 08:47:39 millennia kernel: [17179595.228000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jan 28 08:47:39 millennia kernel: [17179595.236000] input: PC Speaker as /class/input/input1
Jan 28 08:47:39 millennia kernel: [17179595.292000] logips2pp: Detected unknown logitech mouse model 1
Jan 28 08:47:39 millennia kernel: [17179595.316000] **** SET: Misaligned resource pointer: cac44622 Type 07 Len 0
Jan 28 08:47:39 millennia kernel: [17179595.316000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Jan 28 08:47:39 millennia kernel: [17179595.316000] PCI: setting IRQ 11 as level-triggered
Jan 28 08:47:39 millennia kernel: [17179595.316000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jan 28 08:47:39 millennia kernel: [17179595.484000] input: PS/2 Logitech Mouse as /class/input/input2
Jan 28 08:47:39 millennia kernel: [17179595.604000] ts: Compaq touchscreen protocol output
Jan 28 08:47:39 millennia kernel: [17179596.788000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Jan 28 08:47:39 millennia kernel: [17179597.004000] lp0: using parport0 (interrupt-driven).
Jan 28 08:47:39 millennia kernel: [17179597.136000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
Jan 28 08:47:39 millennia kernel: [17179597.296000] EXT3 FS on hda1, internal journal
Jan 28 08:47:39 millennia kernel: [17179597.596000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Jan 28 08:47:39 millennia kernel: [17179597.596000] md: bitmap version 4.39
Jan 28 08:47:39 millennia kernel: [17179597.852000] NET: Registered protocol family 17
Jan 28 08:47:39 millennia kernel: [17179598.256000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Jan 28 08:47:39 millennia kernel: [17179599.144000] cdrom: open failed.
Jan 28 08:47:39 millennia kernel: [17179599.632000] NET: Registered protocol family 10
Jan 28 08:47:39 millennia kernel: [17179599.636000] lo: Disabled Privacy Extensions
Jan 28 08:47:39 millennia kernel: [17179599.636000] IPv6 over IPv4 tunneling driver
Jan 28 08:47:39 millennia kernel: [17179607.224000] ACPI: Power Button (FF) [PWRF]
Jan 28 08:47:39 millennia kernel: [17179607.224000] ACPI: Power Button (CM) [PWRB]
Jan 28 08:47:39 millennia kernel: [17179607.460000] ibm_acpi: ec object not found
Jan 28 08:47:39 millennia kernel: [17179607.516000] pcc_acpi: loading...
Jan 28 08:47:41 millennia kernel: [17179610.504000] eth0: no IPv6 routers present
Jan 28 08:48:41 millennia shutdown[4299]: shutting down for system reboot
J

---

### Post by bscbrit on 2007-01-28
What system / version do you have installed?  Server, Gnome, KDE, whatever?  When you say it becomes unresponsive, do you leave it at the log-on screen, the desktop or running a program?  Is it unresponsive to the keyboard, the mouse, Ctrl-Del-Backspace (X server restart), the power switch?  When it fails to respond, is the screen blank, or displaying a screen-saver?

---

### Post by ffpcs on 2007-01-28
I have a pentium III 256MB RAM 80GIG HD with nVidia TNT Pro graphics adaptor.  I installed ubuntu ver 6.0 LTS.  I am using the default desktop GNOME. I left it at the destop each time. When it is unresponsive, it is unresponsive to everything, mouse, keyboard, etc.  I didn't know about Ctrl-Del-Backspace. I'll try that next time.  The last time it froze, it was at a screensaver.  The only way i could get it back the last time was to hold the power button in until it shut down.  When it came back, it started in "character" mode, not graphical.  Once I gave the command "sudo reboot", it restarted normally (i.e. graphical interface).


"What system / version do you have installed? Server, Gnome, KDE, whatever? When you say it becomes unresponsive, do you leave it at the log-on screen, the desktop or running a program? Is it unresponsive to the keyboard, the mouse, Ctrl-Del-Backspace (X server restart), the power switch? When it fails to respond, is the screen blank, or displaying a screen-saver?"

---

### Post by bscbrit on 2007-01-28
If the machine is doing this every time you leave it, then I suggest that you start the System Monitor (System->System Monitor) and leave it running at the page that shows all the running PIDs etc.  At least that way you will see what is running that might be causing the problem.  

But, in the meantime, try doing a complete update from you apt repositories. e.g. at the command line (Applications->Accessories->Terminal) use the following commands:

sudo apt-get update
sudo apt-get dist-upgrade

to let the system check that it has the latest software installed.  It might be (but I cannot explain why it should be!) that the system has not quite got a clean installation - unlikely but it is worth checking.

Did you install from a live-disk or from packages obtained elsewhere?  Did you install from the standard desktop or alternative desktop disk - if you don't know or are not sure it is probably the former.  Have you got the best kernel installed for your CPU?  Have you installed the nVidia specific drivers?

See if this link helps:

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by ffpcs on 2007-01-28
Thanks for the information.  I was finally able to get the "restricted" updates to install.  These appear to deal with issues related to my nVidia card.  I am going to leave the system idle for the rest of the afternoon and see what happens.  I'll leave an update here tomorrow.  I appreciate your help.

-Frank

> **bscbrit said:**
> If the machine is doing this every time you leave it, then I suggest that you start the System Monitor (System->System Monitor) and leave it running at the page that shows all the running PIDs etc.  At least that way you will see what is running that might be causing the problem.  

But, in the meantime, try doing a complete update from you apt repositories. e.g. at the command line (Applications->Accessories->Terminal) use the following commands:

sudo apt-get update
sudo apt-get dist-upgrade

to let the system check that it has the latest software installed.  It might be (but I cannot explain why it should be!) that the system has not quite got a clean installation - unlikely but it is worth checking.

Did you install from a live-disk or from packages obtained elsewhere?  Did you install from the standard desktop or alternative desktop disk - if you don't know or are not sure it is probably the former.  Have you got the best kernel installed for your CPU?  Have you installed the nVidia specific drivers?

See if this link helps:

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by bscbrit on 2007-01-28
No problems - see you tomorrow perhaps....

---

### Post by ffpcs on 2007-01-29
Just a quick update. Since I successfully installed the restricted updates yesterday, I have NOT had a repeat of my system freezing up.  Perhaps it is too soon to celebrate, but this is the longest it has been running without freezing.

~Frank

---

