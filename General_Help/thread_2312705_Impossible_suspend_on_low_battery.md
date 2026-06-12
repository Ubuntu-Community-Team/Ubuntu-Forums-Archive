---
title: "Impossible suspend on low battery"
date: 2016-02-06
forum: General Help
---

### Post by Louis_Lourdelet on 2016-02-06
Hi everyone,

I have a Lenovo G505s laptop running Windows 10, Ubuntu 14.04 and Kubuntu 15.10 in multi-boot. On both Linux, my laptop can't suspend when battery is low. It actually tries to suspend alone when battery is low, apparently manages to do it as the fans stop themselves just like a normal suspend. But just a second after, it wakes up alone, and doesn't try anymore to suspend. I have the same issue if I try to suspend it by myself. But if the battery isn't low, there is absolutely no sleep issues. 
My processor is an AMD A8-4500M APU with Radeon HD Graphics (I guess the second part is the graphic card), Ubuntu runs with Unity and Kubuntu with Plasma 5. I installed on both systems tlp and cairo-dock, I don't see other programms which could have an impact on this.

Here are the logs from syslog : 

For a failed suspend on low battery :

```
[COLOR=#000000]Jan 31 16:50:15 louis59-Kubuntu15 NetworkManager[759]: <info>  sleep requested (sleeping: no  enabled: yes)
Jan 31 16:50:15 louis59-Kubuntu15 NetworkManager[759]: <info>  sleeping...
Jan 31 16:50:15 louis59-Kubuntu15 NetworkManager[759]: <info>  (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jan 31 16:50:15 louis59-Kubuntu15 NetworkManager[759]: <info>  (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jan 31 16:50:15 louis59-Kubuntu15 NetworkManager[759]: <info>  NetworkManager state is now ASLEEP
Jan 31 16:50:20 louis59-Kubuntu15 systemd[1]: Starting TLP suspend/resume...
Jan 31 16:50:21 louis59-Kubuntu15 systemd[1]: Started TLP suspend/resume.
Jan 31 16:50:21 louis59-Kubuntu15 systemd[1]: Reached target Sleep.
Jan 31 16:50:21 louis59-Kubuntu15 systemd[1]: Starting Suspend...
Jan 31 16:50:21 louis59-Kubuntu15 systemd-sleep[10307]: Suspending system...
Jan 31 16:50:21 louis59-Kubuntu15 kernel: [ 6663.282094] PM: Syncing filesystems ... done.
Jan 31 16:50:21 louis59-Kubuntu15 kernel: [ 6663.600781] PM: Preparing system for sleep (mem)
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6671.750011] Freezing user space processes ... (elapsed 0.003 seconds) done.
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6671.753196] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6671.754793] PM: Suspending system (mem)
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6671.754813] Suspending console(s) (use no_console_suspend to debug)
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6671.755373] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6671.755510] sd 0:0:0:0: [sda] Stopping disk
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.817249] PM: suspend of devices complete after 1062.038 msecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.817848] PM: late suspend of devices complete after 0.594 msecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.819045] ohci-pci 0000:00:13.0: System wakeup enabled by ACPI
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.819105] ohci-pci 0000:00:12.0: System wakeup enabled by ACPI
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.819111] xhci_hcd 0000:00:10.0: System wakeup enabled by ACPI
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.831662] PM: noirq suspend of devices complete after 13.806 msecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.831960] ACPI: Preparing to enter system sleep state S3
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.835423] ACPI : EC: EC stopped
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.835424] PM: Saving platform NVS memory
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.835430] Disabling non-boot CPUs ...
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.837151] smpboot: CPU 1 is now offline
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.853601] smpboot: CPU 2 is now offline
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.868066] Broke affinity for irq 17
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.868089] Broke affinity for irq 29
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.869123] smpboot: CPU 3 is now offline
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884269] ACPI: Low-level resume complete
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884320] ACPI : EC: EC started
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884320] PM: Restoring platform NVS memory
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884341] Using NULL legacy PIC
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884391] LVT offset 0 assigned for vector 0x400
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884455] [Firmware Bug]: cpu 0, try to use APIC500 (LVT offset 0) for vector 0xf9, but the register is already in use for vector 0x400 on another cpu
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884456] [Firmware Bug]: cpu 0, failed to setup threshold interrupt for bank 4, block 0 (MSR00000413=0xc000000001000000)
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884458] [Firmware Bug]: cpu 0, try to use APIC500 (LVT offset 0) for vector 0xf9, but the register is already in use for vector 0x400 on another cpu
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884459] [Firmware Bug]: cpu 0, failed to setup threshold interrupt for bank 4, block 1 (MSRC0000408=0xc000000001000000)
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884494] Enabling non-boot CPUs ...
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884538] x86: Booting SMP configuration:
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.884539] smpboot: Booting Node 0 Processor 1 APIC 0x11
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.892399]  cache: parent cpu1 should not be sleeping
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.892574] CPU1 is up
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.892654] smpboot: Booting Node 0 Processor 2 APIC 0x12
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.904679]  cache: parent cpu2 should not be sleeping
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.904882] CPU2 is up
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.904987] smpboot: Booting Node 0 Processor 3 APIC 0x13
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.916773]  cache: parent cpu3 should not be sleeping
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.916989] CPU3 is up
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.917917] ACPI: Waking up from system sleep state S3
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.921059] ohci-pci 0000:00:12.0: System wakeup disabled by ACPI
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.921080] ohci-pci 0000:00:13.0: System wakeup disabled by ACPI
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.936829] xhci_hcd 0000:00:10.0: System wakeup disabled by ACPI
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.936887] PM: noirq resume of devices complete after 16.027 msecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.937309] PM: early resume of devices complete after 0.385 msecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.940078] ath: phy0: ASPM enabled: 0x43
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6672.947921] sd 0:0:0:0: [sda] Starting disk
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.117090] [drm] PCIE GART of 1024M enabled (table at 0x00000000002E8000).
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.117223] radeon 0000:00:01.0: WB enabled
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.117226] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000030000c00 and cpu addr 0xffff88003f34fc00
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.117961] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90001035a18
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.138020] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000030000c18 and cpu addr 0xffff88003f34fc18
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.138022] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000030000c1c and cpu addr 0xffff88003f34fc1c
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.138025] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000030000c04 and cpu addr 0xffff88003f34fc04
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.138027] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000030000c08 and cpu addr 0xffff88003f34fc08
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.138029] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000030000c0c and cpu addr 0xffff88003f34fc0c
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.138031] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000030000c10 and cpu addr 0xffff88003f34fc10
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.140029] rtc_cmos 00:01: System wakeup disabled by ACPI
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.156639] [drm] ring test on 0 succeeded in 2 usecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.156645] [drm] ring test on 3 succeeded in 3 usecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.156651] [drm] ring test on 4 succeeded in 3 usecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.176014] usb 3-4: reset high-speed USB device number 3 using ehci-pci
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.184043] usb 4-2: reset high-speed USB device number 2 using ehci-pci
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.202341] [drm] ring test on 5 succeeded in 1 usecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.222200] [drm] UVD initialized successfully.
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.331409] [drm:radeon_vce_ring_test [radeon]] *ERROR* radeon: vce failed to lock ring 6 (-12).
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.331439] [drm:cayman_startup [radeon]] *ERROR* radeon: failed initializing VCE (-12).
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.331978] [drm] ib test on ring 0 succeeded in 0 usecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.332521] [drm] ib test on ring 3 succeeded in 0 usecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.333046] [drm] ib test on ring 4 succeeded in 0 usecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.353443] [drm] ib test on ring 5 succeeded
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.436146] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6673.455306] ata2.00: configured for UDMA/100
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6675.564181] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6675.577098] ata1.00: configured for UDMA/100
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6675.645867] PM: resume of devices complete after 2708.316 msecs
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6675.646460] PM: Finishing wakeup.
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6675.646464] Restarting tasks ... done.
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1]: Time has been changed
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6675.704806] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6675.705742] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 31 16:50:36 louis59-Kubuntu15 kernel: [ 6675.706337] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 31 16:50:36 louis59-Kubuntu15 rtkit-daemon[1361]: The canary thread is apparently starving. Taking action.
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1015]: Time has been changed
Jan 31 16:50:36 louis59-Kubuntu15 rtkit-daemon[1361]: Demoting known real-time threads.
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1059]: Time has been changed
Jan 31 16:50:36 louis59-Kubuntu15 rtkit-daemon[1361]: Successfully demoted thread 1382 of process 1360 (n/a).
Jan 31 16:50:36 louis59-Kubuntu15 systemd-sleep[10307]: System resumed.
Jan 31 16:50:36 louis59-Kubuntu15 rtkit-daemon[1361]: Successfully demoted thread 1381 of process 1360 (n/a).
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1]: Started Suspend.
Jan 31 16:50:36 louis59-Kubuntu15 rtkit-daemon[1361]: Successfully demoted thread 1378 of process 1360 (n/a).
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Jan 31 16:50:36 louis59-Kubuntu15 rtkit-daemon[1361]: Successfully demoted thread 1360 of process 1360 (n/a).
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1]: Stopped target Sleep.
Jan 31 16:50:36 louis59-Kubuntu15 rtkit-daemon[1361]: Demoted 4 threads.
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1]: tlp-sleep.service: Unit not needed anymore. Stopping.
Jan 31 16:50:36 louis59-Kubuntu15 NetworkManager[759]: <info>  wake requested (sleeping: yes  enabled: yes)
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1]: Stopping TLP suspend/resume...
Jan 31 16:50:36 louis59-Kubuntu15 NetworkManager[759]: <info>  waking up...
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1]: Reached target Suspend.
Jan 31 16:50:36 louis59-Kubuntu15 NetworkManager[759]: <info>  (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1]: suspend.target: Unit is bound to inactive unit systemd-suspend.service. Stopping, too.
Jan 31 16:50:36 louis59-Kubuntu15 NetworkManager[759]: <info>  (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 31 16:50:36 louis59-Kubuntu15 NetworkManager[759]: <info>  NetworkManager state is now DISCONNECTED
Jan 31 16:50:36 louis59-Kubuntu15 systemd[1]: Stopped TLP suspend/resume.
[/COLOR]
```


For a successfull suspend with enough battery : 

```

[SIZE=2][FONT=arial][COLOR=#000000]Jan 31 17:01:54 louis59-Kubuntu15 NetworkManager[759]: <info>  sleep requested (sleeping: no  enabled: yes)
Jan 31 17:01:54 louis59-Kubuntu15 NetworkManager[759]: <info>  sleeping...
Jan 31 17:01:54 louis59-Kubuntu15 NetworkManager[759]: <info>  (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jan 31 17:01:54 louis59-Kubuntu15 NetworkManager[759]: <info>  (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jan 31 17:01:54 louis59-Kubuntu15 NetworkManager[759]: <info>  NetworkManager state is now ASLEEP
Jan 31 17:01:55 louis59-Kubuntu15 systemd[1]: Starting TLP suspend/resume...
Jan 31 17:01:55 louis59-Kubuntu15 systemd[1]: Started TLP suspend/resume.
Jan 31 17:01:55 louis59-Kubuntu15 systemd[1]: Reached target Sleep.
Jan 31 17:01:55 louis59-Kubuntu15 systemd[1]: Starting Suspend...
Jan 31 17:01:55 louis59-Kubuntu15 systemd-sleep[10693]: Suspending system...
Jan 31 17:01:56 louis59-Kubuntu15 kernel: [ 7355.355434] PM: Syncing filesystems ... done.
Jan 31 17:01:56 louis59-Kubuntu15 kernel: [ 7355.678457] PM: Preparing system for sleep (mem)
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7366.263110] Freezing user space processes ... (elapsed 0.003 seconds) done.
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7366.266281] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7366.267915] PM: Suspending system (mem)
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7366.267938] Suspending console(s) (use no_console_suspend to debug)
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7366.268607] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7366.268709] sd 0:0:0:0: [sda] Stopping disk
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.354398] PM: suspend of devices complete after 1085.948 msecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.355194] PM: late suspend of devices complete after 0.791 msecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.356627] ohci-pci 0000:00:13.0: System wakeup enabled by ACPI
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.356669] ohci-pci 0000:00:12.0: System wakeup enabled by ACPI
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.356706] xhci_hcd 0000:00:10.0: System wakeup enabled by ACPI
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.372587] PM: noirq suspend of devices complete after 17.385 msecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.372846] ACPI: Preparing to enter system sleep state S3
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.376273] ACPI : EC: EC stopped
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.376274] PM: Saving platform NVS memory
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.376280] Disabling non-boot CPUs ...
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.378038] smpboot: CPU 1 is now offline
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.394649] smpboot: CPU 2 is now offline
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.410415] smpboot: CPU 3 is now offline
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425384] ACPI: Low-level resume complete
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425435] ACPI : EC: EC started
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425435] PM: Restoring platform NVS memory
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425456] Using NULL legacy PIC
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425505] LVT offset 0 assigned for vector 0x400
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425568] [Firmware Bug]: cpu 0, try to use APIC500 (LVT offset 0) for vector 0xf9, but the register is already in use for vector 0x400 on another cpu
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425570] [Firmware Bug]: cpu 0, failed to setup threshold interrupt for bank 4, block 0 (MSR00000413=0xc000000001000000)
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425572] [Firmware Bug]: cpu 0, try to use APIC500 (LVT offset 0) for vector 0xf9, but the register is already in use for vector 0x400 on another cpu
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425573] [Firmware Bug]: cpu 0, failed to setup threshold interrupt for bank 4, block 1 (MSRC0000408=0xc000000001000000)
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425607] Enabling non-boot CPUs ...
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425651] x86: Booting SMP configuration:
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.425651] smpboot: Booting Node 0 Processor 1 APIC 0x11
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.437459]  cache: parent cpu1 should not be sleeping
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.437624] CPU1 is up
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.437657] smpboot: Booting Node 0 Processor 2 APIC 0x12
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.449863]  cache: parent cpu2 should not be sleeping
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.450099] CPU2 is up
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.450160] smpboot: Booting Node 0 Processor 3 APIC 0x13
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.461855]  cache: parent cpu3 should not be sleeping
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.462067] CPU3 is up
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.462962] ACPI: Waking up from system sleep state S3
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.466131] ohci-pci 0000:00:12.0: System wakeup disabled by ACPI
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.466180] ohci-pci 0000:00:13.0: System wakeup disabled by ACPI
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.481850] xhci_hcd 0000:00:10.0: System wakeup disabled by ACPI
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.481968] PM: noirq resume of devices complete after 16.028 msecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.482489] PM: early resume of devices complete after 0.483 msecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.485527] ath: phy0: ASPM enabled: 0x43
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.493101] sd 0:0:0:0: [sda] Starting disk
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.662227] [drm] PCIE GART of 1024M enabled (table at 0x00000000002E8000).
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.662361] radeon 0000:00:01.0: WB enabled
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.662365] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000030000c00 and cpu addr 0xffff88003f34fc00
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.663100] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90001035a18
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.683172] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000030000c18 and cpu addr 0xffff88003f34fc18
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.683174] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000030000c1c and cpu addr 0xffff88003f34fc1c
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.683177] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000030000c04 and cpu addr 0xffff88003f34fc04
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.683179] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000030000c08 and cpu addr 0xffff88003f34fc08
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.683181] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000030000c0c and cpu addr 0xffff88003f34fc0c
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.683183] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000030000c10 and cpu addr 0xffff88003f34fc10
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.685156] rtc_cmos 00:01: System wakeup disabled by ACPI
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.701794] [drm] ring test on 0 succeeded in 2 usecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.701801] [drm] ring test on 3 succeeded in 3 usecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.701806] [drm] ring test on 4 succeeded in 3 usecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.721097] usb 3-4: reset high-speed USB device number 3 using ehci-pci
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.733157] usb 4-2: reset high-speed USB device number 2 using ehci-pci
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.747480] [drm] ring test on 5 succeeded in 1 usecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.767353] [drm] UVD initialized successfully.
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.876709] [drm:radeon_vce_ring_test [radeon]] *ERROR* radeon: vce failed to lock ring 6 (-12).
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.876740] [drm:cayman_startup [radeon]] *ERROR* radeon: failed initializing VCE (-12).
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.877280] [drm] ib test on ring 0 succeeded in 0 usecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.877824] [drm] ib test on ring 3 succeeded in 0 usecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.878350] [drm] ib test on ring 4 succeeded in 0 usecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.898748] [drm] ib test on ring 5 succeeded
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7367.981225] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7368.000301] ata2.00: configured for UDMA/100
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7370.053255] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7370.066197] ata1.00: configured for UDMA/100
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7370.185949] PM: resume of devices complete after 2703.218 msecs
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7370.186543] PM: Finishing wakeup.
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7370.186546] Restarting tasks ... done.
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7370.232328] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7370.233331] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 31 17:02:24 louis59-Kubuntu15 kernel: [ 7370.234000] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: Time has been changed
Jan 31 17:02:24 louis59-Kubuntu15 NetworkManager[759]: <info>  wake requested (sleeping: yes  enabled: yes)
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1015]: Time has been changed
Jan 31 17:02:24 louis59-Kubuntu15 NetworkManager[759]: <info>  waking up...
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1059]: Time has been changed
Jan 31 17:02:24 louis59-Kubuntu15 NetworkManager[759]: <info>  (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 31 17:02:24 louis59-Kubuntu15 systemd-sleep[10693]: System resumed.
Jan 31 17:02:24 louis59-Kubuntu15 NetworkManager[759]: <info>  (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: Started Suspend.
Jan 31 17:02:24 louis59-Kubuntu15 NetworkManager[759]: <info>  NetworkManager state is now DISCONNECTED
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: Stopped target Sleep.
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: tlp-sleep.service: Unit not needed anymore. Stopping.
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: Stopping TLP suspend/resume...
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: Reached target Suspend.
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: Stopped target Suspend.
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: Started Run anacron jobs at resume.
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: Started Run anacron jobs.
Jan 31 17:02:24 louis59-Kubuntu15 anacron[10765]: Anacron 2.3 started on 2016-01-31
Jan 31 17:02:24 louis59-Kubuntu15 anacron[10765]: Normal exit (0 jobs run)
Jan 31 17:02:24 louis59-Kubuntu15 systemd[1]: Stopped TLP suspend/resume.
Jan 31 17:02:35 louis59-Kubuntu15 kernel: [ 7381.121592] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
Jan 31 17:02:35 louis59-Kubuntu15 kernel: [ 7381.135031] psmouse serio1: Touchpad at isa0060/serio1/input0 - driver resynced.[/COLOR][/FONT][/SIZE]
```

If anyone understands anything to this, I would be please to have some help ! :-)
Thanks !

PS : as far as English isn't my mother tongue, I apologize if I made any mistake !

---

### Post by Vladlenin5000 on 2016-02-06
> **Louis_Lourdelet said:**
> AMD A8-4500M APU

So, the question is, are you or are you not using the proprietary AMD drivers (fglrx)?
AMD APUs usually require it for optimal graphics performance **and** **power management**.

---

### Post by Louis_Lourdelet on 2016-02-07
Well, I have absolutely no idea of this... Where can I check this ?

Edit: I read this page, apparently I think that if I never installed it by myself, it isn't installed... And I did not install it.
[https://doc.ubuntu-fr.org/catalyst](https://doc.ubuntu-fr.org/catalyst)
But they also say that the driver shouldn't be used for cards older than HD 5000 (I guess mine is a HD 4500 ?)

---

### Post by Vladlenin5000 on 2016-02-07
Yes, it's true that AMD ended support for many legacy GPUs in Linux some time ago and those can now use the default open source *radeon* driver only. This doesn't apply to youi. You have a new APU (CPU+GPU+several functions otherwise managed by the chipset in the same chip) so it's almost a must to have the proprietary drivers (fglrx) instead.

System Settings > Software & Updates (14.04) > Additional drivers
System Settings > Software Properties (15.10) > Additional drivers (Kubuntu is probably different, just search "additional drivers")

Select and apply both *fglrx* and *AMD microcode*.

---

### Post by Louis_Lourdelet on 2016-03-05
Ok thanks a lot, I found it, I'll see if it changes anything !! I'm sorry for the answer time, I am a bit busy these days...

---

