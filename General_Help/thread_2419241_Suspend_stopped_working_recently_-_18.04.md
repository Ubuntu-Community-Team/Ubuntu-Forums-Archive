---
title: "Suspend stopped working recently - 18.04"
date: 2019-05-18
forum: General Help
---

### Post by sorceror171 on 2019-05-18
Suspend has always been a *little* flaky on my machine. (ASUS P8Z68-V PRO/GEN3 motherboard, i7-2600K, 16GB RAM, Nvidia GTX 970) Usually I could get about five suspends before it would stop successfully shutting down the disks, fans, and CPU. Then I'd have to reboot the machine.

Sometime in the last couple weeks (not sure exactly, been traveling a bunch), suspend stopped working entirely. The screens go black, but the case lights and fans keep going. This is kind of annoying, as I don't want to leave the thing on all the time sucking power when I'm not using it... but I also don't want to have to boot the thing up and restart all my apps when I come back.

I don't see anything obvious in dmesg, or /var/log/syslog or /var/log/kern.log - though I'm not quite sure what I should be looking for. How can I debug a suspend problem like this?

---

### Post by sorceror171 on 2019-05-19
Here's what happens when I try to suspend:

[FONT=Courier New][ 2022.216686] PM: suspend entry (deep)
[ 2022.216688] PM: Syncing filesystems ... done.
[ 2022.832002] Freezing user space processes ... (elapsed 0.001 seconds) done.
[ 2022.833526] OOM killer disabled.
[ 2022.833527] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[ 2022.834629] Suspending console(s) (use no_console_suspend to debug)
[ 2022.838894] e1000e: EEE TX LPI TIMER: 00000011
[ 2022.911330] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
[ 2022.911330] sd 4:0:0:0: [sdd] Synchronizing SCSI cache
[ 2022.911351] sd 2:0:0:0: [sdc] Synchronizing SCSI cache
[ 2022.911359] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2022.911360] sd 5:0:0:0: [sde] Synchronizing SCSI cache
[ 2022.911491] sd 4:0:0:0: [sdd] Stopping disk
[ 2022.911500] sd 5:0:0:0: [sde] Stopping disk
[ 2022.911556] sd 2:0:0:0: [sdc] Stopping disk
[ 2022.912784] sd 1:0:0:0: [sdb] Stopping disk
[ 2022.915608] sd 0:0:0:0: [sda] Stopping disk
[ 2022.979311] pci_pm_suspend(): hcd_pci_suspend+0x0/0x30 returns -16
[ 2022.979315] dpm_run_callback(): pci_pm_suspend+0x0/0x150 returns -16
[ 2022.979318] PM: Device 0000:04:00.0 failed to suspend async: error -16
[ 2023.923296] snd_hda_intel 0000:01:00.1: spurious response 0x1:0x0, last cmd=0x5f2f05
[ 2023.923297] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f2f05
[ 2023.923298] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f2f05
[ 2023.923299] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f2f05
[ 2023.923300] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f2f05
[ 2023.923301] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f2f05
[ 2023.923302] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f2f05
[ 2023.923303] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f2f05
[ 2023.923304] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f2f05
[ 2023.923305] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f2f05
[ 2023.923309] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 5
[ 2025.939367] snd_hda_intel 0000:01:00.1: azx_get_response timeout, switching to polling mode: last cmd=0x004f0900
[ 2026.947382] snd_hda_intel 0000:01:00.1: azx_get_response timeout, switching to single_cmd mode: last cmd=0x004f0900
[ 2026.947483] azx_single_wait_for_response: 13 callbacks suppressed
[ 2026.947486] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD buf size -1
[ 2026.947683] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD buf size -1
[ 2026.947794] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD buf size -1
[ 2026.947913] PM: Some devices failed to suspend, or early wake event detected
[ 2026.948165] usb usb3: root hub lost power or was reset
[ 2026.948168] usb usb4: root hub lost power or was reset
[ 2026.948242] usb usb7: root hub lost power or was reset
[ 2026.948244] usb usb8: root hub lost power or was reset
[ 2026.961105] sd 0:0:0:0: [sda] Starting disk
[ 2026.961124] sd 1:0:0:0: [sdb] Starting disk
[ 2026.961140] sd 2:0:0:0: [sdc] Starting disk
[ 2026.961168] sd 4:0:0:0: [sdd] Starting disk
[ 2026.961189] sd 5:0:0:0: [sde] Starting disk
[ 2027.095357] usb 2-1.5: reset full-speed USB device number 5 using ehci-pci
[ 2027.219797] usb 5-3.4: reset high-speed USB device number 4 using xhci_hcd
[ 2027.261578] ata8: SATA link down (SStatus 0 SControl 300)
[ 2027.261797] ata7: SATA link down (SStatus 0 SControl 300)
[ 2027.285819] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 2027.285843] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2027.285864] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 2027.287425] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2027.287436] No Local Variables are initialized for Method [_GTF]
[ 2027.287438] No Arguments are initialized for method [_GTF]
[ 2027.287440] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT1._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2027.287542] ata2.00: supports DRM functions and may not be fully accessible
[ 2027.288321] ata2.00: disabling queued TRIM support
[ 2027.290144] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2027.290154] No Local Variables are initialized for Method [_GTF]
[ 2027.290156] No Arguments are initialized for method [_GTF]
[ 2027.290158] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT1._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2027.290202] ata2.00: supports DRM functions and may not be fully accessible
[ 2027.290486] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2027.290496] No Local Variables are initialized for Method [_GTF]
[ 2027.290498] No Arguments are initialized for method [_GTF]
[ 2027.290500] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT0._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2027.290807] ata2.00: disabling queued TRIM support
[ 2027.292223] ata2.00: configured for UDMA/133
[ 2027.293978] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2027.293988] No Local Variables are initialized for Method [_GTF]
[ 2027.293990] No Arguments are initialized for method [_GTF]
[ 2027.293992] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT3._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2027.297107] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2027.297115] No Local Variables are initialized for Method [_GTF]
[ 2027.297117] No Arguments are initialized for method [_GTF]
[ 2027.297120] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT0._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2027.297910] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2027.297917] No Local Variables are initialized for Method [_GTF]
[ 2027.297919] No Arguments are initialized for method [_GTF]
[ 2027.297922] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT3._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2027.297934] ata4.00: configured for UDMA/133
[ 2027.298099] ata1.00: configured for UDMA/133
[ 2027.332520] usblp3: removed
[ 2027.332633] usblp4: removed
[ 2027.609541] usblp 5-3.4:1.1: usblp3: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5912
[ 2027.610472] usblp 5-3.4:1.3: usblp4: USB Bidirectional printer dev 4 if 3 alt 0 proto 2 vid 0x03F0 pid 0x5912
[ 2027.789370] OOM killer enabled.
[ 2027.789371] Restarting tasks ... done.
[ 2027.791152] PM: suspend exit
[ 2027.791188] PM: suspend entry (shallow)
[ 2027.791189] PM: Syncing filesystems ... 
[ 2027.992640] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 1
[ 2029.783623] snd_hdac_bus_update_rirb: 499 callbacks suppressed
[ 2029.783625] snd_hda_intel 0000:01:00.1: spurious response 0x80000000:0x0, last cmd=0x4f0900
[ 2029.831056] snd_hda_intel 0000:01:00.1: spurious response 0x80000000:0x0, last cmd=0x5f0900
[ 2029.881288] snd_hda_intel 0000:01:00.1: spurious response 0xc0000000:0x0, last cmd=0x5f2e08
[ 2029.881325] snd_hda_intel 0000:01:00.1: spurious response 0x5f:0x0, last cmd=0x5f2f00
[ 2029.881371] snd_hda_intel 0000:01:00.1: spurious response 0x80000010:0x0, last cmd=0x5f2f01
[ 2029.881374] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 1
[ 2029.881433] snd_hda_intel 0000:01:00.1: spurious response 0x80000000:0x0, last cmd=0x4f0900
[ 2029.881435] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x4f0900
[ 2030.141416] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 2030.203565] snd_hda_intel 0000:01:00.1: spurious response 0x5f:0x0, last cmd=0x5f2f00
[ 2030.203600] snd_hda_intel 0000:01:00.1: spurious response 0x80000010:0x0, last cmd=0x5f2f01
[ 2030.203641] snd_hda_intel 0000:01:00.1: spurious response 0x80000000:0x0, last cmd=0x5f2f02
[ 2030.733272] done.
[ 2030.895140] Freezing user space processes ... (elapsed 0.001 seconds) done.
[ 2030.896818] OOM killer disabled.
[ 2030.896818] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[ 2030.897942] Suspending console(s) (use no_console_suspend to debug)
[ 2030.904635] e1000e: EEE TX LPI TIMER: 00000011
[ 2032.951545] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2032.955889] sd 0:0:0:0: [sda] Stopping disk
[ 2032.959601] sd 2:0:0:0: [sdc] Synchronizing SCSI cache
[ 2032.961108] sd 2:0:0:0: [sdc] Stopping disk
[ 2032.963602] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
[ 2032.963604] sd 4:0:0:0: [sdd] Synchronizing SCSI cache
[ 2032.963629] sd 5:0:0:0: [sde] Synchronizing SCSI cache
[ 2032.963749] sd 4:0:0:0: [sdd] Stopping disk
[ 2032.963817] sd 5:0:0:0: [sde] Stopping disk
[ 2032.965674] sd 1:0:0:0: [sdb] Stopping disk
[ 2033.971895] ACPI: EC: interrupt blocked
[ 2033.991997] ACPI: Preparing to enter system sleep state S1
[ 2033.992366] ACPI: EC: event blocked
[ 2033.992366] ACPI: EC: EC stopped
[ 2033.992367] PM: Saving platform NVS memory
[ 2033.992392] Disabling non-boot CPUs ...
[ 2034.008821] smpboot: CPU 1 is now offline
[ 2034.032851] smpboot: CPU 2 is now offline
[ 2034.056886] smpboot: CPU 3 is now offline
[ 2034.081020] smpboot: CPU 4 is now offline
[ 2034.103821] IRQ 23: no longer affine to CPU5
[ 2034.103843] IRQ 38: no longer affine to CPU5
[ 2034.103859] IRQ 52: no longer affine to CPU5
[ 2034.104865] smpboot: CPU 5 is now offline
[ 2034.127817] IRQ 16: no longer affine to CPU6
[ 2034.127823] IRQ 19: no longer affine to CPU6
[ 2034.127839] IRQ 33: no longer affine to CPU6
[ 2034.127860] IRQ 48: no longer affine to CPU6
[ 2034.128869] smpboot: CPU 6 is now offline
[ 2034.151819] IRQ 39: no longer affine to CPU7
[ 2034.152852] smpboot: CPU 7 is now offline
[ 2050.748650] ACPI: EC: EC started
[ 2050.748651] PM: Restoring platform NVS memory
[ 2050.749031] Enabling non-boot CPUs ...
[ 2050.749128] x86: Booting SMP configuration:
[ 2050.749130] smpboot: Booting Node 0 Processor 1 APIC 0x2
[ 2050.751961]  cache: parent cpu1 should not be sleeping
[ 2050.752228] CPU1 is up
[ 2050.752275] smpboot: Booting Node 0 Processor 2 APIC 0x4
[ 2050.755144]  cache: parent cpu2 should not be sleeping
[ 2050.755448] CPU2 is up
[ 2050.755485] smpboot: Booting Node 0 Processor 3 APIC 0x6
[ 2050.758286]  cache: parent cpu3 should not be sleeping
[ 2050.758594] CPU3 is up
[ 2050.758633] smpboot: Booting Node 0 Processor 4 APIC 0x1
[ 2050.761553]  cache: parent cpu4 should not be sleeping
[ 2050.761878] CPU4 is up
[ 2050.761903] smpboot: Booting Node 0 Processor 5 APIC 0x3
[ 2050.764291]  cache: parent cpu5 should not be sleeping
[ 2050.764469] CPU5 is up
[ 2050.764492] smpboot: Booting Node 0 Processor 6 APIC 0x5
[ 2050.766902]  cache: parent cpu6 should not be sleeping
[ 2050.767086] CPU6 is up
[ 2050.767110] smpboot: Booting Node 0 Processor 7 APIC 0x7
[ 2050.769499]  cache: parent cpu7 should not be sleeping
[ 2050.769696] CPU7 is up
[ 2050.775236] ACPI: Waking up from system sleep state S1
[ 2050.775738] ACPI: EC: interrupt unblocked
[ 2050.796615] ACPI: EC: event unblocked
[ 2050.806796] sd 0:0:0:0: [sda] Starting disk
[ 2050.806829] sd 4:0:0:0: [sdd] Starting disk
[ 2050.806841] sd 1:0:0:0: [sdb] Starting disk
[ 2050.806849] sd 5:0:0:0: [sde] Starting disk
[ 2050.807133] sd 2:0:0:0: [sdc] Starting disk
[ 2051.055627] usb 5-3.4: reset high-speed USB device number 4 using xhci_hcd
[ 2051.109751] ata7: SATA link down (SStatus 0 SControl 300)
[ 2051.109794] ata8: SATA link down (SStatus 0 SControl 300)
[ 2051.168185] usblp3: removed
[ 2051.168277] usblp4: removed
[ 2051.177649] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2051.177764] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2051.177785] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 2051.177812] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 2051.177836] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2051.177858] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2051.178151] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.178164] No Local Variables are initialized for Method [_GTF]
[ 2051.178166] No Arguments are initialized for method [_GTF]
[ 2051.178169] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT2._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.178274] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.178283] No Local Variables are initialized for Method [_GTF]
[ 2051.178285] No Arguments are initialized for method [_GTF]
[ 2051.178287] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT5._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.178964] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.178976] No Local Variables are initialized for Method [_GTF]
[ 2051.178978] No Arguments are initialized for method [_GTF]
[ 2051.178981] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.179361] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.179373] No Local Variables are initialized for Method [_GTF]
[ 2051.179375] No Arguments are initialized for method [_GTF]
[ 2051.179378] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT1._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.179480] ata2.00: supports DRM functions and may not be fully accessible
[ 2051.180172] ata2.00: disabling queued TRIM support
[ 2051.180704] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.180716] No Local Variables are initialized for Method [_GTF]
[ 2051.180718] No Arguments are initialized for method [_GTF]
[ 2051.180721] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.181002] ata5.00: configured for UDMA/133
[ 2051.181722] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.181731] No Local Variables are initialized for Method [_GTF]
[ 2051.181733] No Arguments are initialized for method [_GTF]
[ 2051.181735] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT1._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.181774] ata2.00: supports DRM functions and may not be fully accessible
[ 2051.182266] ata2.00: disabling queued TRIM support
[ 2051.182336] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.182344] No Local Variables are initialized for Method [_GTF]
[ 2051.182346] No Arguments are initialized for method [_GTF]
[ 2051.182349] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT0._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.183523] ata2.00: configured for UDMA/133
[ 2051.184273] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.184281] No Local Variables are initialized for Method [_GTF]
[ 2051.184283] No Arguments are initialized for method [_GTF]
[ 2051.184285] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT0._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.185258] ata1.00: configured for UDMA/133
[ 2051.185970] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.185979] No Local Variables are initialized for Method [_GTF]
[ 2051.185981] No Arguments are initialized for method [_GTF]
[ 2051.185983] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT3._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.189925] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2051.189934] No Local Variables are initialized for Method [_GTF]
[ 2051.189936] No Arguments are initialized for method [_GTF]
[ 2051.189938] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT3._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2051.189951] ata4.00: configured for UDMA/133
[ 2051.487527] usblp 5-3.4:1.1: usblp3: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5912
[ 2051.550936] usblp 5-3.4:1.3: usblp4: USB Bidirectional printer dev 4 if 3 alt 0 proto 2 vid 0x03F0 pid 0x5912
[ 2051.825683] OOM killer enabled.
[ 2051.825684] Restarting tasks ... done.
[ 2051.826906] PM: suspend exit
[ 2053.921333] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 2054.937157] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2054.937174] No Local Variables are initialized for Method [_GTF]
[ 2054.937176] No Arguments are initialized for method [_GTF]
[ 2054.937180] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT2._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2054.937447] ata3.00: configured for UDMA/133
[ 2055.041139] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[ 2055.041157] No Local Variables are initialized for Method [_GTF]
[ 2055.041159] No Arguments are initialized for method [_GTF]
[ 2055.041162] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT5._GTF, AE_NOT_FOUND (20170831/psparse-550)
[ 2055.041432] ata6.00: configured for UDMA/133
[ 2063.659133] e1000e: eno1 NIC Link is Down
[ 2063.663453] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[ 2063.891683] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[ 2067.418598] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 2067.418641] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[ 2067.419259] snd_hdac_bus_update_rirb: 215 callbacks suppressed
[ 2067.419263] snd_hda_intel 0000:01:00.1: spurious response 0x80000000:0x0, last cmd=0x4f0900
[ 2067.478554] snd_hda_intel 0000:01:00.1: spurious response 0x80000000:0x0, last cmd=0x5f0900
[ 2067.529366] snd_hda_intel 0000:01:00.1: spurious response 0xc0000000:0x0, last cmd=0x5f2e08
[ 2067.529371] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD buf size 67108864
[ 2067.529428] snd_hda_intel 0000:01:00.1: spurious response 0x5f:0x0, last cmd=0x4f0900
[ 2067.529431] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x4f0900
[ 2067.855581] snd_hda_intel 0000:01:00.1: spurious response 0x5f:0x0, last cmd=0x5f2f00
[ 2067.855616] snd_hda_intel 0000:01:00.1: spurious response 0x80000010:0x0, last cmd=0x5f2f01
[ 2067.855657] snd_hda_intel 0000:01:00.1: spurious response 0x80000000:0x0, last cmd=0x5f2f02
[ 2067.855699] snd_hda_intel 0000:01:00.1: spurious response 0x80000008:0x0, last cmd=0x5f2f03
[ 2067.855740] snd_hda_intel 0000:01:00.1: spurious response 0x80000000:0x0, last cmd=0x5f2f04[/FONT]

---

### Post by thehipho on 2019-05-19
Hi, also check pm-suspend.log for any possible clues? Most issues are probably video card related!

```
cat /var/log/pm-suspend.log
```

---

### Post by sorceror171 on 2019-05-19
I'm afraid the file you specified doesn't exist:

```
ls /var/log/pm-suspend.log
ls: cannot access '/var/log/pm-suspend.log': No such file or directory
```

However, I *did* manage to figure something out. The line from the log I posted earlier:

```
[ 2022.979318] PM: Device 0000:04:00.0 failed to suspend async: error -16
```

...led me to grep the output of 'lshw'. Turns out it's the extra USB-3 controller card in there. But that's been in there for years now, so it's not the problem by itself. What *has* changed in the last couple weeks is me hooking up an HP Officejet Pro 8600 Plus *printer* to that controller.

So, as an experiment, I rejiggered the USB cables in back of the desktop. Now, that printer is hooked up to the motherboard USB-2 controller... and suspend works. (Well, at least, as well as it did before. We'll see how many suspend cycles I can get before I have to reboot.) The printer's only USB-2 anyway, so no loss.

---

### Post by thehipho on 2019-05-19
Ok glad to hear, you’re tracking down the cause of this problem.

---

