---
title: "Hibernation/hybrid-sleep stresses harddisk/HDD by triggering spindown + spinup"
date: 2024-04-24
forum: General Help
---

### Post by talcid on 2024-04-24
Hey everybody,

when telling my system to enter or exit hybrid-sleep mode, my harddisk  goes through an additional spindown and a second later a spinup, which  will wear down the motor much quicker. This seems to happen while the  contents of the RAM are being written/read while entering or resuming  hybrid-sleep mode.

I can also hear my optical drive clicking and my RGB mouse flashing for a  moment when the harddisk is spinning down and spinning up again.

My system has an SSD, a HDD and an optical drive. The system partition  and swap partition are on the SSD. The HDD is only used for additional  storage and backups.

I'm not exactly sure where to look for further help with this problem  and if this even might be a bug. Maybe the fine people in this forum can  provide some help.

I'm using Kubuntu 23.10.

Kernel:
```
Linux Hostname 6.5.0-28-generic #29-Ubuntu SMP PREEMPT_DYNAMIC Thu Mar 28 23:46:48 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux&#8203;
```

Here is an except from my log. Let me know, if you need more information.

```
2024-04-21T01:23:52.469581+02:00 Hostname systemd[1]: Reached target sleep.target - Sleep.
2024-04-21T01:23:52.508953+02:00 Hostname systemd[1]: Starting systemd-hybrid-sleep.service - Hybrid Suspend+Hibernate...
2024-04-21T01:23:52.520421+02:00 Hostname kernel: [45022.301747] PM: Image not found (code -16)
2024-04-21T01:23:52.553765+02:00 Hostname plasmashell[2076]: qt.qpa.clipboard: QXcbClipboard::setMimeData: Cannot set X11 selection owner
2024-04-21T01:23:52.573965+02:00 Hostname plasmashell[2076]: qt.qpa.clipboard: QXcbClipboard::setMimeData: Cannot set X11 selection owner
2024-04-21T01:23:52.781109+02:00 Hostname systemd-sleep[93191]: Entering sleep state 'hybrid-sleep'...
2024-04-21T01:23:52.783952+02:00 Hostname kernel: [45022.566573] PM: hibernation: hibernation entry
2024-04-21T01:23:52.803965+02:00 Hostname kernel: [45022.589530] Filesystems sync: 0.022 seconds
2024-04-21T01:23:52.803998+02:00 Hostname kernel: [45022.589627] Freezing user space processes
2024-04-21T12:04:53.824423+02:00 Hostname kernel: [45022.595012] Freezing user space processes completed (elapsed 0.005 seconds)
2024-04-21T12:04:53.824451+02:00 Hostname kernel: [45022.595024] OOM killer disabled.
2024-04-21T12:04:53.824454+02:00 Hostname kernel: [45022.595211] PM: hibernation: Marking nosave pages: [mem 0x00000000-0x00000fff]
2024-04-21T12:04:53.825861+02:00 Hostname kernel: [45022.595215] PM: hibernation: Marking nosave pages: [mem 0x00090000-0x00090fff]
2024-04-21T12:04:53.825872+02:00 Hostname kernel: [45022.595216] PM: hibernation: Marking nosave pages: [mem 0x0009e000-0x000fffff]
2024-04-21T12:04:53.831457+02:00 Hostname kernel: [45022.595219] PM: hibernation: Marking nosave pages: [mem 0x20000000-0x201fffff]
2024-04-21T12:04:53.831471+02:00 Hostname kernel: [45022.595227] PM: hibernation: Marking nosave pages: [mem 0x40004000-0x40004fff]
2024-04-21T12:04:53.910741+02:00 Hostname kernel: [45022.595228] PM: hibernation: Marking nosave pages: [mem 0xcc4d9000-0xcd803fff]
2024-04-21T12:04:53.910755+02:00 Hostname kernel: [45022.595286] PM: hibernation: Marking nosave pages: [mem 0xcd805000-0xcd847fff]
2024-04-21T12:04:53.911770+02:00 Hostname kernel: [45022.595288] PM: hibernation: Marking nosave pages: [mem 0xcdc7b000-0xcdff3fff]
2024-04-21T12:04:53.911779+02:00 Hostname kernel: [45022.595299] PM: hibernation: Marking nosave pages: [mem 0xce000000-0xffffffff]
2024-04-21T12:04:53.916345+02:00 Hostname kernel: [45022.596016] PM: hibernation: Basic memory bitmaps created
2024-04-21T12:04:53.916359+02:00 Hostname kernel: [45022.596017] PM: hibernation: Preallocating image memory
2024-04-21T12:04:53.916417+02:00 Hostname kernel: [45077.009448] PM: hibernation: Allocated 1563807 pages for snapshot
2024-04-21T12:04:53.916419+02:00 Hostname kernel: [45077.009454] PM: hibernation: Allocated 6255228 kbytes in 54.41 seconds (114.96 MB/s)
2024-04-21T12:04:53.916419+02:00 Hostname kernel: [45077.009456] Freezing remaining freezable tasks
2024-04-21T12:04:53.916420+02:00 Hostname kernel: [45078.126482] Freezing remaining freezable tasks completed (elapsed 1.117 seconds)
2024-04-21T12:04:53.916433+02:00 Hostname kernel: [45078.126856] printk: Suspending console(s) (use no_console_suspend to debug)
2024-04-21T12:04:53.916435+02:00 Hostname kernel: [45078.128192] serial 00:06: disabled
2024-04-21T12:04:53.916436+02:00 Hostname kernel: [45078.150451] ata6.00: Entering standby power mode
2024-04-21T12:04:53.916437+02:00 Hostname kernel: [45078.150475] ata2.00: Entering standby power mode
2024-04-21T12:04:53.916438+02:00 Hostname kernel: [45078.576755] Disabling non-boot CPUs ...
2024-04-21T12:04:53.916439+02:00 Hostname kernel: [45078.579206] smpboot: CPU 1 is now offline
2024-04-21T12:04:53.916447+02:00 Hostname kernel: [45078.581447] smpboot: CPU 2 is now offline
2024-04-21T12:04:53.916448+02:00 Hostname kernel: [45078.584279] smpboot: CPU 3 is now offline
2024-04-21T12:04:53.916450+02:00 Hostname kernel: [45078.586578] smpboot: CPU 4 is now offline
2024-04-21T12:04:53.916451+02:00 Hostname kernel: [45078.588804] smpboot: CPU 5 is now offline
2024-04-21T12:04:53.916452+02:00 Hostname kernel: [45078.591012] smpboot: CPU 6 is now offline
2024-04-21T12:04:53.916452+02:00 Hostname kernel: [45078.593152] smpboot: CPU 7 is now offline
2024-04-21T12:04:53.916453+02:00 Hostname kernel: [45078.593809] PM: hibernation: Creating image:
2024-04-21T12:04:53.916454+02:00 Hostname kernel: [45079.145521] PM: hibernation: Need to copy 1517335 pages
2024-04-21T12:04:53.945338+02:00 Hostname kernel: [45079.145528] PM: hibernation: Normal pages needed: 1517335 + 1024, available pages: 2595976
2024-04-21T12:04:53.945359+02:00 Hostname kernel: [45078.594589] Enabling non-boot CPUs ...
2024-04-21T12:04:53.945360+02:00 Hostname kernel: [45078.594686] smpboot: Booting Node 0 Processor 1 APIC 0x2
2024-04-21T12:04:53.945361+02:00 Hostname kernel: [45078.598130] CPU1 is up
2024-04-21T12:04:53.945361+02:00 Hostname kernel: [45078.598191] smpboot: Booting Node 0 Processor 2 APIC 0x4
2024-04-21T12:04:53.945362+02:00 Hostname kernel: [45078.601407] CPU2 is up
2024-04-21T12:04:53.945363+02:00 Hostname kernel: [45078.601476] smpboot: Booting Node 0 Processor 3 APIC 0x6
2024-04-21T12:04:53.945363+02:00 Hostname kernel: [45078.604700] CPU3 is up
2024-04-21T12:04:53.945364+02:00 Hostname kernel: [45078.604756] smpboot: Booting Node 0 Processor 4 APIC 0x1
2024-04-21T12:04:53.945364+02:00 Hostname kernel: [45078.608513] CPU4 is up
2024-04-21T12:04:53.945365+02:00 Hostname kernel: [45078.608574] smpboot: Booting Node 0 Processor 5 APIC 0x3
2024-04-21T12:04:53.945366+02:00 Hostname kernel: [45078.611874] CPU5 is up
2024-04-21T12:04:53.945366+02:00 Hostname kernel: [45078.611937] smpboot: Booting Node 0 Processor 6 APIC 0x5
2024-04-21T12:04:53.945367+02:00 Hostname kernel: [45078.615261] CPU6 is up
2024-04-21T12:04:53.945368+02:00 Hostname kernel: [45078.615326] smpboot: Booting Node 0 Processor 7 APIC 0x7
2024-04-21T12:04:53.945368+02:00 Hostname kernel: [45078.618692] CPU7 is up
2024-04-21T12:04:53.945369+02:00 Hostname kernel: [45078.970916] usb usb2: root hub lost power or was reset
2024-04-21T12:04:53.945369+02:00 Hostname kernel: [45078.970924] usb usb3: root hub lost power or was reset
2024-04-21T12:04:53.945370+02:00 Hostname kernel: [45078.970929] usb usb1: root hub lost power or was reset
2024-04-21T12:04:53.945372+02:00 Hostname kernel: [45078.970931] usb usb4: root hub lost power or was reset
2024-04-21T12:04:53.945372+02:00 Hostname kernel: [45078.973200] serial 00:06: activated
2024-04-21T12:04:53.945373+02:00 Hostname kernel: [45079.267175] usb 1-1: reset high-speed USB device number 2 using ehci-pci
2024-04-21T12:04:53.945373+02:00 Hostname kernel: [45079.267189] usb 2-1: reset high-speed USB device number 2 using ehci-pci
2024-04-21T12:04:53.945374+02:00 Hostname kernel: [45079.313618] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
2024-04-21T12:04:53.945374+02:00 Hostname kernel: [45079.313628] ata2.00: Entering active power mode
2024-04-21T12:04:53.945378+02:00 Hostname kernel: [45079.313645] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
2024-04-21T12:04:53.945379+02:00 Hostname kernel: [45079.313671] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
2024-04-21T12:04:53.945380+02:00 Hostname kernel: [45079.313680] ata6.00: Entering active power mode
2024-04-21T12:04:53.945380+02:00 Hostname kernel: [45079.315685] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT1._GTF.DSSP], AE_NOT_FOUND (20230331/psargs-330)
2024-04-21T12:04:53.945381+02:00 Hostname kernel: [45079.315702]
2024-04-21T12:04:53.945382+02:00 Hostname kernel: [45079.315705] No Local Variables are initialized for Method [_GTF]
2024-04-21T12:04:53.961392+02:00 Hostname kernel: [45079.315706]
2024-04-21T12:04:53.961402+02:00 Hostname kernel: [45079.315708] No Arguments are initialized for method [_GTF]
2024-04-21T12:04:53.961404+02:00 Hostname kernel: [45079.315709]
2024-04-21T12:04:53.961405+02:00 Hostname kernel: [45079.315711] ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT1._GTF due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
2024-04-21T12:04:53.961406+02:00 Hostname kernel: [45079.315813] ata2.00: supports DRM functions and may not be fully accessible
2024-04-21T12:04:53.961406+02:00 Hostname kernel: [45079.316475] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT4._GTF.DSSP], AE_NOT_FOUND (20230331/psargs-330)
2024-04-21T12:04:53.962309+02:00 Hostname kernel: [45079.316491]
2024-04-21T12:04:53.962315+02:00 Hostname kernel: [45079.316494] No Local Variables are initialized for Method [_GTF]
2024-04-21T12:04:53.962316+02:00 Hostname kernel: [45079.316495]
2024-04-21T12:04:53.962317+02:00 Hostname kernel: [45079.316496] No Arguments are initialized for method [_GTF]
2024-04-21T12:04:53.962318+02:00 Hostname kernel: [45079.316497]
2024-04-21T12:04:53.962318+02:00 Hostname kernel: [45079.316500] ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT4._GTF due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
2024-04-21T12:04:53.962320+02:00 Hostname kernel: [45079.320027] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT1._GTF.DSSP], AE_NOT_FOUND (20230331/psargs-330)
2024-04-21T12:04:53.963833+02:00 Hostname kernel: [45079.320043]
2024-04-21T12:04:53.963854+02:00 Hostname kernel: [45079.320045] No Local Variables are initialized for Method [_GTF]
2024-04-21T12:04:53.963856+02:00 Hostname kernel: [45079.320047]
2024-04-21T12:04:53.963857+02:00 Hostname kernel: [45079.320048] No Arguments are initialized for method [_GTF]
2024-04-21T12:04:53.963858+02:00 Hostname kernel: [45079.320050]
2024-04-21T12:04:53.963859+02:00 Hostname kernel: [45079.320052] ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT1._GTF due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
2024-04-21T12:04:53.963860+02:00 Hostname kernel: [45079.320131] ata2.00: supports DRM functions and may not be fully accessible
2024-04-21T12:04:53.963861+02:00 Hostname kernel: [45079.320321] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT4._GTF.DSSP], AE_NOT_FOUND (20230331/psargs-330)
2024-04-21T12:04:53.963862+02:00 Hostname kernel: [45079.320337]
2024-04-21T12:04:53.963863+02:00 Hostname kernel: [45079.320339] No Local Variables are initialized for Method [_GTF]
2024-04-21T12:04:53.963864+02:00 Hostname kernel: [45079.320341]
2024-04-21T12:04:53.963865+02:00 Hostname kernel: [45079.320342] No Arguments are initialized for method [_GTF]
2024-04-21T12:04:53.963865+02:00 Hostname kernel: [45079.320343]
2024-04-21T12:04:53.963866+02:00 Hostname kernel: [45079.320346] ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT4._GTF due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
2024-04-21T12:04:53.963867+02:00 Hostname kernel: [45079.320363] ata5.00: configured for UDMA/100
2024-04-21T12:04:53.963868+02:00 Hostname kernel: [45079.324342] ata2.00: configured for UDMA/133
2024-04-21T12:04:53.965283+02:00 Hostname kernel: [45079.324645] ata2.00: Enabling discard_zeroes_data
2024-04-21T12:04:53.965287+02:00 Hostname kernel: [45079.931202] usb 1-1.7: reset low-speed USB device number 3 using ehci-pci
2024-04-21T12:04:53.965287+02:00 Hostname kernel: [45080.307204] usb 1-1.8: reset full-speed USB device number 4 using ehci-pci
2024-04-21T12:04:53.965288+02:00 Hostname kernel: [45080.418326] PM: hibernation: Basic memory bitmaps freed
2024-04-21T12:04:53.965288+02:00 Hostname kernel: [45080.418482] OOM killer enabled.
2024-04-21T12:04:53.965298+02:00 Hostname kernel: [45080.418484] Restarting tasks ... done.
2024-04-21T12:04:53.965299+02:00 Hostname kernel: [45080.430557] PM: hibernation: hibernation exit
2024-04-21T12:04:54.023043+02:00 Hostname systemd-resolved[1055]: Clock change detected. Flushing caches.
2024-04-21T12:04:54.023574+02:00 Hostname rtkit-daemon[1663]: The canary thread is apparently starving. Taking action.
2024-04-21T12:04:54.023949+02:00 Hostname systemd-sleep[93191]: System returned from sleep state.
2024-04-21T12:04:54.024034+02:00 Hostname rtkit-daemon[1663]: Demoting known real-time threads.
2024-04-21T12:04:54.024339+02:00 Hostname systemd[1]: Started anacron.service - Run anacron jobs.
2024-04-21T12:04:54.026580+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 19785 of process 6397.
2024-04-21T12:04:54.026767+02:00 Hostname systemd[1]: Starting apt-daily-upgrade.service - Daily apt upgrade and clean activities...
2024-04-21T12:04:54.026942+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 10342 of process 5435.
2024-04-21T12:04:54.027197+02:00 Hostname systemd[1]: Starting e2scrub_all.service - Online ext4 Metadata Check for All Filesystems...
2024-04-21T12:04:54.027334+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 9111 of process 5606.
2024-04-21T12:04:54.027542+02:00 Hostname systemd[1]: Starting fwupd-refresh.service - Refresh fwupd metadata and update motd...
2024-04-21T12:04:54.034434+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 9047 of process 5468.
2024-04-21T12:04:54.034713+02:00 Hostname systemd[1]: Starting motd-news.service - Message of the Day...
2024-04-21T12:04:54.034826+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 9046 of process 5624.
2024-04-21T12:04:54.034906+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 9045 of process 5669.
2024-04-21T12:04:54.034981+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 5280 of process 5052.
2024-04-21T12:04:54.035055+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 1793 of process 1776.
2024-04-21T12:04:54.035153+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 1776 of process 1776.
2024-04-21T12:04:54.035275+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 1791 of process 1773.
2024-04-21T12:04:54.037026+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 1773 of process 1773.
2024-04-21T12:04:54.037081+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 1789 of process 1775.
2024-04-21T12:04:54.037145+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 1775 of process 1775.
2024-04-21T12:04:54.037241+02:00 Hostname rtkit-daemon[1663]: Successfully demoted thread 1784 of process 1774.
2024-04-21T12:04:54.037308+02:00 Hostname rtkit-daemon[1663]: Demoted 14 threads.
2024-04-21T12:04:54.037693+02:00 Hostname anacron[93314]: Anacron 2.3 started on 2024-04-21
2024-04-21T12:04:54.043033+02:00 Hostname anacron[93314]: Will run job `cron.daily' in 5 min.
2024-04-21T12:04:54.043110+02:00 Hostname anacron[93314]: Jobs will be executed sequentially
2024-04-21T12:04:54.089103+02:00 Hostname systemd[1]: Starting plocate-updatedb.service - Update the plocate database...
2024-04-21T12:04:54.092326+02:00 Hostname systemd[1]: Starting man-db.service - Daily man-db regeneration...
2024-04-21T12:04:54.094085+02:00 Hostname systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
2024-04-21T12:04:54.095487+02:00 Hostname systemd[1]: e2scrub_all.service: Deactivated successfully.
2024-04-21T12:04:54.095705+02:00 Hostname systemd[1]: Finished e2scrub_all.service - Online ext4 Metadata Check for All Filesystems.
2024-04-21T12:04:54.096528+02:00 Hostname systemd[1]: motd-news.service: Deactivated successfully.
2024-04-21T12:04:54.096708+02:00 Hostname systemd[1]: Finished motd-news.service - Message of the Day.
2024-04-21T12:04:54.248119+02:00 Hostname systemd[1]: systemd-hybrid-sleep.service: Deactivated successfully.
2024-04-21T12:04:54.248382+02:00 Hostname systemd[1]: Finished systemd-hybrid-sleep.service - Hybrid Suspend+Hibernate.
2024-04-21T12:04:54.248993+02:00 Hostname systemd[1]: systemd-hybrid-sleep.service: Consumed 8.530s CPU time.
2024-04-21T12:04:54.249119+02:00 Hostname systemd[1]: Reached target hybrid-sleep.target - Hybrid Suspend+Hibernate.
2024-04-21T12:04:54.249260+02:00 Hostname systemd[1]: Stopped target sleep.target - Sleep.&#8203; 
```

---

