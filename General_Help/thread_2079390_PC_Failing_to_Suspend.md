---
title: "PC Failing to Suspend"
date: 2012-11-01
forum: General Help
---

### Post by PaperProjects on 2012-11-01
**System:** Ubuntu 12.04 LTS running Ubuntu 2D Shell

Unlike most people, whose computer just has issues with waking up after suspending. My PC won't even suspend or hibernate at all most of the time, though waking up after the times it does work is virtually flawless.

This is what usually happens after clicking the Suspend or Hibernate button. The PC screen turns black for a varying amount of seconds, then turns back on to my desktop with the screen locked. This happens regardless of the mouse or keyboard movement. The mouse and keyboard don't even affect the process because even in Windows my PC requires that you press the power button to wake it up.

This is rather problematic because there is no error message whatsoever and the issue forces me to shut down my PC and reboot it which is slow.

---

### Post by bastos77 on 2012-11-03
sounds like i have the same problem...

---

### Post by schnurrbidurr on 2012-11-04
I have the exactly the same problem. I had it with Kubuntu, Ubuntu 12.10 (running Unity) and 12.04 (Gnome and Unity). 
But I did not have it running Opensuse and KDE (My hardware has not changed).

Below is a part of the log file

> Nov  4 11:31:42 cellar NetworkManager[880]: <info> sleep requested (sleeping: no  enabled: yes)
Nov  4 11:31:42 cellar NetworkManager[880]: <info> sleeping or disabling...
Nov  4 11:31:42 cellar NetworkManager[880]: <info> (eth0): now unmanaged
Nov  4 11:31:42 cellar NetworkManager[880]: <info> (eth0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Nov  4 11:31:42 cellar NetworkManager[880]: <info> (eth0): deactivating device (reason 'sleeping') [37]
Nov  4 11:31:42 cellar NetworkManager[880]: <info> (eth0): canceled DHCP transaction, DHCP client pid 3118
Nov  4 11:31:42 cellar avahi-daemon[878]: Withdrawing address record for fe80::226:18ff:fe77:76f8 on eth0.
Nov  4 11:31:42 cellar avahi-daemon[878]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::226:18ff:fe77:76f8.
Nov  4 11:31:42 cellar avahi-daemon[878]: Interface eth0.IPv6 no longer relevant for mDNS.
Nov  4 11:31:42 cellar avahi-daemon[878]: Withdrawing address record for 192.168.0.4 on eth0.
Nov  4 11:31:42 cellar avahi-daemon[878]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.4.
Nov  4 11:31:42 cellar avahi-daemon[878]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov  4 11:31:42 cellar NetworkManager[880]: <info> DNS: starting dnsmasq...
Nov  4 11:31:42 cellar dnsmasq[3131]: exiting on receipt of SIGTERM
Nov  4 11:31:42 cellar NetworkManager[880]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Nov  4 11:31:42 cellar dnsmasq[4625]: started, version 2.59 cache disabled
Nov  4 11:31:42 cellar dnsmasq[4625]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Nov  4 11:31:42 cellar dnsmasq[4625]: warning: no upstream servers configured
Nov  4 11:31:42 cellar NetworkManager[880]: <info> (eth0): cleaning up...
Nov  4 11:31:42 cellar NetworkManager[880]: <info> (eth0): taking down device.
Nov  4 11:31:42 cellar dbus[835]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov  4 11:31:42 cellar NetworkManager[880]: <info> (eth0): carrier now OFF (device state 10)
Nov  4 11:31:42 cellar dbus[835]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov  4 11:31:43 cellar anacron[4713]: Anacron 2.3 started on 2012-11-04
Nov  4 11:31:43 cellar anacron[4713]: Normal exit (0 jobs run)
Nov  4 11:31:51 cellar kernel: [  844.744556] PM: Syncing filesystems ... done.
Nov  4 11:31:51 cellar kernel: [  844.746905] PM: Preparing system for mem sleep
Nov  4 11:31:51 cellar kernel: [  844.746915] Freezing user space processes ... (elapsed 0.01 seconds) done.
Nov  4 11:31:51 cellar kernel: [  844.760069] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Nov  4 11:31:51 cellar kernel: [  844.776070] PM: Entering mem sleep
Nov  4 11:31:51 cellar kernel: [  844.776088] Suspending console(s) (use no_console_suspend to debug)
Nov  4 11:31:51 cellar kernel: [  844.776519] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
Nov  4 11:31:51 cellar kernel: [  844.776609] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov  4 11:31:51 cellar kernel: [  844.776938] serial 00:09: disabled
Nov  4 11:31:51 cellar kernel: [  844.776943] serial 00:09: wake-up capability disabled by ACPI
Nov  4 11:31:51 cellar kernel: [  844.778112] sd 0:0:0:0: [sda] Stopping disk
Nov  4 11:31:51 cellar kernel: [  844.796093] ohci_hcd 0000:00:02.0: PCI INT A disabled
Nov  4 11:31:51 cellar kernel: [  844.821861] sd 2:0:0:0: [sdb] Stopping disk
Nov  4 11:31:51 cellar kernel: [  844.856046] ehci_hcd 0000:00:02.1: PCI INT B disabled
Nov  4 11:31:51 cellar kernel: [  845.045912] PM: suspend of drv:sd dev:0:0:0:0 complete after 269.301 msecs
Nov  4 11:31:51 cellar kernel: [  845.045949] PM: suspend of drv:scsi dev:target0:0:0 complete after 269.275 msecs
Nov  4 11:31:51 cellar kernel: [  845.045961] PM: suspend of drv:scsi dev:host0 complete after 269.254 msecs
Nov  4 11:31:51 cellar kernel: [  845.076045] PM: suspend of drv:pata_amd dev:0000:00:06.0 complete after 298.625 msecs
Nov  4 11:31:51 cellar kernel: [  845.172055] snd_hda_intel 0000:00:05.0: PCI INT B disabled
Nov  4 11:31:51 cellar kernel: [  845.188044] PM: suspend of drv:snd_hda_intel dev:0000:00:05.0 complete after 410.604 msecs
Nov  4 11:31:51 cellar kernel: [  845.431463] PM: suspend of drv:sd dev:2:0:0:0 complete after 654.946 msecs
Nov  4 11:31:51 cellar kernel: [  845.431499] PM: suspend of drv:scsi dev:target2:0:0 complete after 654.907 msecs
Nov  4 11:31:51 cellar kernel: [  845.431510] PM: suspend of drv:scsi dev:host2 complete after 654.822 msecs
Nov  4 11:31:51 cellar kernel: [  845.431596] sata_nv 0000:00:08.0: PCI INT A disabled
Nov  4 11:31:51 cellar kernel: [  845.444045] PM: suspend of drv:sata_nv dev:0000:00:08.0 complete after 666.928 msecs
Nov  4 11:31:51 cellar kernel: [  845.444082] PM: suspend of drv: dev:pci0000:00 complete after 666.576 msecs
Nov  4 11:31:51 cellar kernel: [  845.444091] PM: suspend of devices complete after 667.872 msecs
Nov  4 11:31:51 cellar kernel: [  845.444093] PM: suspend devices took 0.668 seconds
Nov  4 11:31:51 cellar kernel: [  845.460073] ehci_hcd 0000:00:02.1: PME# enabled
Nov  4 11:31:51 cellar kernel: [  845.460084] ehci_hcd 0000:00:02.1: wake-up capability enabled by ACPI
Nov  4 11:31:51 cellar kernel: [  845.476060] ohci_hcd 0000:00:02.0: PME# enabled
Nov  4 11:31:51 cellar kernel: [  845.476071] ohci_hcd 0000:00:02.0: wake-up capability enabled by ACPI
Nov  4 11:31:51 cellar kernel: [  845.492131] PM: late suspend of devices complete after 48.032 msecs
Nov  4 11:31:51 cellar kernel: [  845.492196] ACPI: Preparing to enter system sleep state S3
Nov  4 11:31:51 cellar kernel: [  845.493011] PM: Saving platform NVS memory
Nov  4 11:31:51 cellar kernel: [  845.493151] Disabling non-boot CPUs ...
Nov  4 11:31:51 cellar kernel: [  845.596030] CPU 1 is now offline
Nov  4 11:31:51 cellar kernel: [  845.596345] ACPI: Low-level resume complete
Nov  4 11:31:51 cellar kernel: [  845.596345] PM: Restoring platform NVS memory
Nov  4 11:31:51 cellar kernel: [  845.596345] Enabling non-boot CPUs ...
Nov  4 11:31:51 cellar kernel: [  845.596345] Booting Node 0 Processor 1 APIC 0x1
Nov  4 11:31:51 cellar kernel: [  845.596345] smpboot cpu 1: start_ip = 97000
Nov  4 11:31:51 cellar kernel: [  845.494457] Initializing CPU#1
Nov  4 11:31:51 cellar kernel: [  845.494457] Calibrating delay loop (skipped) already calibrated this CPU
Nov  4 11:31:51 cellar kernel: [  845.494457] [Firmware Bug]: cpu 1, try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for vector 0xf9 on another cpu
Nov  4 11:31:51 cellar kernel: [  845.494457] perf: IBS APIC setup failed on cpu #1
Nov  4 11:31:51 cellar kernel: [  845.628412] NMI watchdog enabled, takes one hw-pmu counter.
Nov  4 11:31:51 cellar kernel: [  845.632095] CPU1 is up
Nov  4 11:31:51 cellar kernel: [  845.632556] ACPI: Waking up from system sleep state S3
Nov  4 11:31:51 cellar kernel: [  845.633561] ohci_hcd 0000:00:02.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
Nov  4 11:31:51 cellar kernel: [  845.633572] ohci_hcd 0000:00:02.0: wake-up capability disabled by ACPI
Nov  4 11:31:51 cellar kernel: [  845.633575] ohci_hcd 0000:00:02.0: PME# disabled
Nov  4 11:31:51 cellar kernel: [  845.633589] ehci_hcd 0000:00:02.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
Nov  4 11:31:51 cellar kernel: [  845.633600] ehci_hcd 0000:00:02.1: wake-up capability disabled by ACPI
Nov  4 11:31:51 cellar kernel: [  845.633602] ehci_hcd 0000:00:02.1: PME# disabled
Nov  4 11:31:51 cellar kernel: [  845.633655] pci 0000:00:00.0: Found enabled HT MSI Mapping
Nov  4 11:31:51 cellar kernel: [  845.633669] snd_hda_intel 0000:00:05.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
Nov  4 11:31:51 cellar kernel: [  845.633718] pci 0000:00:00.0: Found enabled HT MSI Mapping
Nov  4 11:31:51 cellar kernel: [  845.633797] pci 0000:00:00.0: Found enabled HT MSI Mapping
Nov  4 11:31:51 cellar kernel: [  845.633860] pci 0000:00:00.0: Found enabled HT MSI Mapping
Nov  4 11:31:51 cellar kernel: [  845.633870] pcieport 0000:00:09.0: restoring config space at offset 0x7 (was 0xe1e1, writing 0x2000e1e1)
Nov  4 11:31:51 cellar kernel: [  845.633874] pcieport 0000:00:09.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Nov  4 11:31:51 cellar kernel: [  845.633937] pci 0000:00:00.0: Found enabled HT MSI Mapping
Nov  4 11:31:51 cellar kernel: [  845.633949] pcieport 0000:00:0b.0: restoring config space at offset 0x1 (was 0x100004, writing 0x100404)
Nov  4 11:31:51 cellar kernel: [  845.634015] pci 0000:00:00.0: Found enabled HT MSI Mapping
Nov  4 11:31:51 cellar kernel: [  845.634026] pcieport 0000:00:0c.0: restoring config space at offset 0x1 (was 0x100004, writing 0x100404)
Nov  4 11:31:51 cellar kernel: [  845.634096] pci 0000:00:00.0: Found enabled HT MSI Mapping
Nov  4 11:31:51 cellar kernel: [  845.634128] nvidia 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Nov  4 11:31:51 cellar kernel: [  845.634133] nvidia 0000:02:00.0: restoring config space at offset 0x9 (was 0x1, writing 0xec01)
Nov  4 11:31:51 cellar kernel: [  845.634136] nvidia 0000:02:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xdc000004)
Nov  4 11:31:51 cellar kernel: [  845.634140] nvidia 0000:02:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xc000000c)
Nov  4 11:31:51 cellar kernel: [  845.634143] nvidia 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xdf000000)
Nov  4 11:31:51 cellar kernel: [  845.634147] nvidia 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
Nov  4 11:31:51 cellar kernel: [  845.634264] PM: early resume of devices complete after 0.851 msecs
Nov  4 11:31:51 cellar kernel: [  845.634359] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
Nov  4 11:31:51 cellar kernel: [  845.634365] ohci_hcd 0000:00:02.0: setting latency timer to 64
Nov  4 11:31:51 cellar kernel: [  845.634384] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
Nov  4 11:31:51 cellar kernel: [  845.634389] ehci_hcd 0000:00:02.1: setting latency timer to 64
Nov  4 11:31:51 cellar kernel: [  845.634389] pci 0000:00:04.0: setting latency timer to 64
Nov  4 11:31:51 cellar kernel: [  845.634893] pata_amd 0000:00:06.0: setting latency timer to 64
Nov  4 11:31:51 cellar kernel: [  845.634914] snd_hda_intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
Nov  4 11:31:51 cellar kernel: [  845.634917] snd_hda_intel 0000:00:05.0: setting latency timer to 64
Nov  4 11:31:51 cellar kernel: [  845.634945] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 21 (level, low) -> IRQ 21
Nov  4 11:31:51 cellar kernel: [  845.634947] sata_nv 0000:00:08.0: setting latency timer to 64
Nov  4 11:31:51 cellar kernel: [  845.635865] ata2: port disabled--ignoring
Nov  4 11:31:51 cellar kernel: [  845.635886] sd 0:0:0:0: [sda] Starting disk
Nov  4 11:31:51 cellar kernel: [  845.636842] serial 00:09: activated
Nov  4 11:31:51 cellar kernel: [  845.636960] sd 2:0:0:0: [sdb] Starting disk
Nov  4 11:31:51 cellar kernel: [  845.783003] PM: resume of drv:nvidia dev:0000:02:00.0 complete after 148.527 msecs
Nov  4 11:31:51 cellar kernel: [  845.840064] PM: resume of drv: dev:ep_00 complete after 204.184 msecs
Nov  4 11:31:51 cellar kernel: [  845.840075] PM: resume of drv:hub dev:2-0:1.0 complete after 205.135 msecs
Nov  4 11:31:51 cellar kernel: [  845.840107] PM: resume of drv: dev:ep_81 complete after 205.150 msecs
Nov  4 11:31:51 cellar kernel: [  845.908081] PM: resume of drv:hub dev:1-0:1.0 complete after 267.995 msecs
Nov  4 11:31:51 cellar kernel: [  845.908096] PM: resume of drv: dev:ep_00 complete after 264.042 msecs
Nov  4 11:31:51 cellar kernel: [  845.908110] PM: resume of drv: dev:ep_81 complete after 268.026 msecs
Nov  4 11:31:51 cellar kernel: [  845.908745] PM: resume of drv:hub dev:1-3:1.0 complete after 260.593 msecs
Nov  4 11:31:51 cellar kernel: [  845.908752] PM: resume of drv: dev:ep_00 complete after 260.571 msecs
Nov  4 11:31:51 cellar kernel: [  845.908763] PM: resume of drv: dev:ep_81 complete after 260.603 msecs
Nov  4 11:31:51 cellar kernel: [  845.961128] PM: resume of drv: dev:ep_00 complete after 312.767 msecs
Nov  4 11:31:51 cellar kernel: [  845.961135] PM: resume of drv:usbhid dev:2-4:1.2 complete after 312.795 msecs
Nov  4 11:31:51 cellar kernel: [  845.961139] PM: resume of drv:usbhid dev:2-4:1.0 complete after 312.850 msecs
Nov  4 11:31:51 cellar kernel: [  845.961146] PM: resume of drv: dev:ep_81 complete after 312.850 msecs
Nov  4 11:31:51 cellar kernel: [  845.961148] PM: resume of drv:usbhid dev:2-4:1.1 complete after 312.840 msecs
Nov  4 11:31:51 cellar kernel: [  845.961155] PM: resume of drv: dev:ep_83 complete after 312.811 msecs
Nov  4 11:31:51 cellar kernel: [  845.961158] PM: resume of drv: dev:ep_82 complete after 312.837 msecs
Nov  4 11:31:51 cellar kernel: [  846.020056] usb 1-1: reset high-speed USB device number 2 using ehci_hcd
Nov  4 11:31:51 cellar kernel: [  846.100089] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  4 11:31:51 cellar kernel: [  846.108167] ata4.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
Nov  4 11:31:51 cellar kernel: [  846.108171] ata4.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Nov  4 11:31:51 cellar kernel: [  846.156431] PM: resume of drv:forcedeth dev:0000:00:07.0 complete after 522.020 msecs
Nov  4 11:31:51 cellar kernel: [  846.156466] PM: resume of drv:net dev:eth0 complete after 500.303 msecs
Nov  4 11:31:51 cellar kernel: [  846.264055] usb 1-8: reset high-speed USB device number 6 using ehci_hcd
Nov  4 11:31:51 cellar kernel: [  846.292167] ata4.00: configured for UDMA/100
Nov  4 11:31:51 cellar kernel: [  846.293828] snd-usb-audio 1-1:1.2: no reset_resume for driver snd-usb-audio?
Nov  4 11:31:51 cellar kernel: [  846.293832] snd-usb-audio 1-1:1.3: no reset_resume for driver snd-usb-audio?
Nov  4 11:31:51 cellar kernel: [  846.294004] PM: resume of drv:uvcvideo dev:1-1:1.0 complete after 649.927 msecs
Nov  4 11:31:51 cellar kernel: [  846.294009] PM: resume of drv:usb dev:1-1:1.3 complete after 645.900 msecs
Nov  4 11:31:51 cellar kernel: [  846.294015] PM: resume of drv:uvcvideo dev:1-1:1.1 complete after 645.964 msecs
Nov  4 11:31:51 cellar kernel: [  846.294018] PM: resume of drv: dev:ep_00 complete after 645.895 msecs
Nov  4 11:31:51 cellar kernel: [  846.294020] PM: resume of drv:usb dev:1-1:1.2 complete after 645.966 msecs
Nov  4 11:31:51 cellar kernel: [  846.294038] PM: resume of drv: dev:ep_87 complete after 649.958 msecs
Nov  4 11:31:51 cellar kernel: [  846.950227] PM: resume of drv: dev:ep_00 complete after 1301.965 msecs
Nov  4 11:31:51 cellar kernel: [  846.950236] PM: resume of drv:ums-realtek dev:1-8:1.0 complete after 1302.037 msecs
Nov  4 11:31:51 cellar kernel: [  846.950246] PM: resume of drv: dev:ep_01 complete after 1302.011 msecs
Nov  4 11:31:51 cellar kernel: [  846.950252] PM: resume of drv:scsi dev:host10 complete after 1302.036 msecs
Nov  4 11:31:51 cellar kernel: [  846.950255] PM: resume of drv: dev:ep_82 complete after 1302.004 msecs
Nov  4 11:31:51 cellar kernel: [  846.950276] PM: resume of drv:scsi_host dev:host10 complete after 1302.053 msecs
Nov  4 11:31:51 cellar kernel: [  846.950279] PM: resume of drv:scsi dev:target10:0:0 complete after 1301.909 msecs
Nov  4 11:31:51 cellar kernel: [  846.950291] PM: resume of drv:sd dev:10:0:0:0 complete after 1301.909 msecs
Nov  4 11:31:51 cellar kernel: [  846.950298] PM: resume of drv:scsi_device dev:10:0:0:0 complete after 1301.903 msecs
Nov  4 11:31:51 cellar kernel: [  847.272061] usb 2-6: reset low-speed USB device number 13 using ohci_hcd
Nov  4 11:31:51 cellar kernel: [  847.634122] PM: resume of drv:usbhid dev:2-6:1.0 complete after 1985.698 msecs
Nov  4 11:31:51 cellar kernel: [  847.634128] PM: resume of drv: dev:ep_00 complete after 1985.652 msecs
Nov  4 11:31:51 cellar kernel: [  847.634131] PM: resume of drv: dev:ep_81 complete after 1985.699 msecs
Nov  4 11:31:51 cellar kernel: [  847.634139] PM: resume of drv:usbhid dev:2-6:1.1 complete after 1985.694 msecs
Nov  4 11:31:51 cellar kernel: [  847.634148] PM: resume of drv: dev:ep_82 complete after 1985.691 msecs
Nov  4 11:31:51 cellar kernel: [  847.780067] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  4 11:31:51 cellar kernel: [  847.788163] ata3.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
Nov  4 11:31:51 cellar kernel: [  847.788167] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Nov  4 11:31:51 cellar kernel: [  847.820467] ata3.00: configured for UDMA/133
Nov  4 11:31:51 cellar kernel: [  847.826257] PM: resume of drv:sd dev:2:0:0:0 complete after 2189.292 msecs
Nov  4 11:31:51 cellar kernel: [  847.826287] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 2189.312 msecs
Nov  4 11:31:51 cellar kernel: [  850.108354] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Nov  4 11:31:51 cellar kernel: [  850.108358] ata1.00: ACPI cmd ef/03:01:00:00:00:a0 (SET FEATURES) filtered out
Nov  4 11:31:51 cellar kernel: [  850.108781] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
Nov  4 11:31:51 cellar kernel: [  850.108785] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Nov  4 11:31:51 cellar kernel: [  850.117619] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:900:0x11)
Nov  4 11:31:51 cellar kernel: [  850.133537] ata1.00: configured for UDMA/100
Nov  4 11:31:51 cellar kernel: [  850.136994] PM: resume of drv:sd dev:0:0:0:0 complete after 4501.103 msecs
Nov  4 11:31:51 cellar kernel: [  850.137012] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 3980.523 msecs
Nov  4 11:31:51 cellar kernel: [  850.137026] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 4500.076 msecs
Nov  4 11:31:51 cellar kernel: [  850.137119] PM: resume of devices complete after 4502.815 msecs
Nov  4 11:31:51 cellar kernel: [  850.389860] PM: resume devices took 4.756 seconds
Nov  4 11:31:51 cellar kernel: [  850.389893] PM: Finishing wakeup.
Nov  4 11:31:51 cellar kernel: [  850.389894] Restarting tasks ... done.
Nov  4 11:31:51 cellar acpid: client 4193[0:0] has disconnected
Nov  4 11:31:51 cellar acpid: client 4193[0:0] has disconnected
Nov  4 11:31:51 cellar acpid: client connected from 4193[0:0]
Nov  4 11:31:51 cellar acpid: 1 client rule loaded
Nov  4 11:31:51 cellar acpid: client connected from 4193[0:0]
Nov  4 11:31:51 cellar acpid: 1 client rule loaded
Nov  4 11:31:52 cellar anacron[5201]: Anacron 2.3 started on 2012-11-04
Nov  4 11:31:52 cellar anacron[5201]: Normal exit (0 jobs run)
Nov  4 11:31:53 cellar anacron[5347]: Anacron 2.3 started on 2012-11-04
Nov  4 11:31:53 cellar anacron[5347]: Normal exit (0 jobs run)
Nov  4 11:31:53 cellar NetworkManager[880]: <info> wake requested (sleeping: yes  enabled: yes)
Nov  4 11:31:53 cellar NetworkManager[880]: <info> waking up and re-enabling...
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): now managed
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): bringing up device.
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): carrier now ON (device state 20)
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): preparing device.
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): deactivating device (reason 'managed') [2]
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Auto-activating connection 'Wired connection 1'.
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) starting connection 'Wired connection 1'
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov  4 11:31:53 cellar kernel: [  851.688246] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
Nov  4 11:31:53 cellar NetworkManager[880]: <info> dhclient started with pid 5427
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Beginning IP6 addrconf.
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov  4 11:31:53 cellar dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Nov  4 11:31:53 cellar dhclient: Copyright 2004-2011 Internet Systems Consortium.
Nov  4 11:31:53 cellar dhclient: All rights reserved.
Nov  4 11:31:53 cellar dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Nov  4 11:31:53 cellar dhclient: 
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Nov  4 11:31:53 cellar dhclient: Listening on LPF/eth0/00:26:18:77:76:f8
Nov  4 11:31:53 cellar dhclient: Sending on   LPF/eth0/00:26:18:77:76:f8
Nov  4 11:31:53 cellar dhclient: Sending on   Socket/fallback
Nov  4 11:31:53 cellar dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 255.255.255.255 port 67
Nov  4 11:31:53 cellar dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Nov  4 11:31:53 cellar dhclient: bound to 192.168.0.4 -- renewal in 122005 seconds.
Nov  4 11:31:53 cellar NetworkManager[880]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Nov  4 11:31:53 cellar NetworkManager[880]: <info>   address 192.168.0.4
Nov  4 11:31:53 cellar NetworkManager[880]: <info>   prefix 24 (255.255.255.0)
Nov  4 11:31:53 cellar NetworkManager[880]: <info>   gateway 192.168.0.1
Nov  4 11:31:53 cellar NetworkManager[880]: <info>   nameserver '193.238.80.30'
Nov  4 11:31:53 cellar NetworkManager[880]: <info>   nameserver '91.212.90.30'
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov  4 11:31:53 cellar NetworkManager[880]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Nov  4 11:31:53 cellar avahi-daemon[878]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.4.
Nov  4 11:31:53 cellar avahi-daemon[878]: New relevant interface eth0.IPv4 for mDNS.
Nov  4 11:31:53 cellar avahi-daemon[878]: Registering new address record for 192.168.0.4 on eth0.IPv4.
Nov  4 11:31:54 cellar NetworkManager[880]: <info> DNS: starting dnsmasq...
Nov  4 11:31:54 cellar dnsmasq[4625]: exiting on receipt of SIGTERM
Nov  4 11:31:54 cellar NetworkManager[880]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Nov  4 11:31:54 cellar dnsmasq[5430]: started, version 2.59 cache disabled
Nov  4 11:31:54 cellar dnsmasq[5430]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Nov  4 11:31:54 cellar dnsmasq[5430]: using nameserver 91.212.90.30#53
Nov  4 11:31:54 cellar dnsmasq[5430]: using nameserver 193.238.80.30#53
Nov  4 11:31:54 cellar NetworkManager[880]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  4 11:31:54 cellar NetworkManager[880]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  4 11:31:54 cellar NetworkManager[880]: <info> Activation (eth0) successful, device activated.
Nov  4 11:31:54 cellar NetworkManager[880]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Nov  4 11:31:54 cellar avahi-daemon[878]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::226:18ff:fe77:76f8.
Nov  4 11:31:54 cellar avahi-daemon[878]: New relevant interface eth0.IPv6 for mDNS.
Nov  4 11:31:54 cellar avahi-daemon[878]: Registering new address record for fe80::226:18ff:fe77:76f8 on eth0.*.
Nov  4 11:32:02 cellar ntpdate[5465]: adjust time server 91.189.94.4 offset 0.458679 sec
Nov  4 11:32:03 cellar kernel: [  861.896024] eth0: no IPv6 routers present
Nov  4 11:32:08 cellar kernel: [  867.556854] sd 10:0:0:0: [sdc] Test WP failed, assume Write Enabled
Nov  4 11:32:08 cellar kernel: [  867.558349] sd 10:0:0:0: [sdc] Asking for cache data failed
Nov  4 11:32:08 cellar kernel: [  867.558354] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Nov  4 11:32:13 cellar NetworkManager[880]: <info> (eth0): IP6 addrconf timed out or failed.
Nov  4 11:32:13 cellar NetworkManager[880]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov  4 11:32:13 cellar NetworkManager[880]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov  4 11:32:13 cellar NetworkManager[880]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov  4 11:33:01 cellar kernel: [  919.780964] sd 10:0:0:0: [sdc] Test WP failed, assume Write Enabled
Nov  4 11:33:01 cellar kernel: [  919.782457] sd 10:0:0:0: [sdc] Asking for cache data failed
Nov  4 11:33:01 cellar kernel: [  919.782462] sd 10:0:0:0: [sdc] Assuming drive cache: write through


---

### Post by broken plastic on 2012-11-05
I have the same problem. 12.4 studio never really suspended for me, it only turned off the screen, but hibernate worked.  upon upgrading to 12.10 ubuntu, both suspend and hibernate just flash a black screen and go to log in window.

however, a live version of 12.10 studio appears to work.

asus n76vz (ivy bridge, nvidia gt650m)

---

### Post by schnurrbidurr on 2012-11-06
After reading you answer I was looking for the hibernate button, but hit  suspend by mistake. Guess what? It worked. It suspends and I can wake  it up with the keyboard.
I did some "research" and it turns out, it  has to do with the card reader. 
I'll explain: I have a wireless keyboard  (plugged directly into the motherboard) and a usb mouse with a dongle  that plugs into a usb slot. Up until yesterday I had it plugged into the usb slot on my card reader. But for no particular reason I decided to plug it into the usb slot on my monitor.
To cut a long story short:
When the mouse dongle is plugged into the monitor, suspend works. When I put it back into the card reader, suspend does not work.

I have no idea why that should be. I'm simply not techie enough.

Not sure if it's relevant, but it is a Realtek card reader and the syslog keeps spewing out this message:
> Nov  6 11:03:08 cellar kernel: [ 3138.788537] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
Nov  6 11:03:08 cellar kernel: [ 3138.790081] sd 4:0:0:0: [sdc] Asking for cache data failed
Nov  6 11:03:08 cellar kernel: [ 3138.790086] sd 4:0:0:0: [sdc] Assuming drive cache: write through

---

### Post by PaperProjects on 2012-11-08
Oh, for me, it just turns black and if it fails it'll say "Broken Pipe" etc. and turn back on. Sometimes, I wake up the computer or log off after successful suspends and it may say "Broken Pipe" then it'll stop working again. If I'm lucky after a restart or two it'll work again for a while until the next "Broken Pipe". Oh, also weird stuff like "HDIO failed:" and "Starting Preload", or whatnot "Hdio" being above the broken pipe message and "preload" below.

---

