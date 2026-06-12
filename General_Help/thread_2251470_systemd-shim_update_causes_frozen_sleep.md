---
title: "systemd-shim update causes frozen sleep"
date: 2014-11-04
forum: General Help
---

### Post by Brandon_MacEachern on 2014-11-04
I made a bug report for this:  [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1389306](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1389306)

[COLOR=#333333][FONT=monospace]Since systemd-shim was updated, my laptop is now unable to properly sleep, or wake from sleep. It keeps going to a frozen black screen with a TTY style text cursor just frozen (not blinking). Going to TTY1 lets me type in my username with a frozen non blinking cursor, but the password prompt never appears.[/FONT][/COLOR]

---

### Post by Brandon_MacEachern on 2014-11-04
So what can I do?  Nothing is logged whatsoever.

This is my work laptop and I am loosing time, having to shut down, boot up, shut down, boot up.

---

### Post by Brandon_MacEachern on 2014-11-05
I finally got a log out of it.  While the shim update has caused the issues, it seems to be something to do with the wireless adapter.

```
Nov  5 00:06:32 BrandonsLinuxLaptop NetworkManager[1125]: <info> Writing DNS information to /sbin/resolvconfNov  5 00:06:32 BrandonsLinuxLaptop dnsmasq[1735]: setting upstream servers from DBus
Nov  5 00:06:32 BrandonsLinuxLaptop dnsmasq[1735]: using nameserver 2001:470:4:184:4af8:b3ff:feb1:959a#53
Nov  5 00:06:32 BrandonsLinuxLaptop kernel: [  995.371134] cfg80211: Calling CRDA to update world regulatory domain
Nov  5 00:06:32 BrandonsLinuxLaptop NetworkManager[1125]: <warn> DNS: plugin dnsmasq update failed
Nov  5 00:06:32 BrandonsLinuxLaptop NetworkManager[1125]: <info> Removing DNS information from /sbin/resolvconf
Nov  5 00:06:32 BrandonsLinuxLaptop dnsmasq[1735]: setting upstream servers from DBus
Nov  5 00:06:32 BrandonsLinuxLaptop kernel: [  995.403879] cfg80211: World regulatory domain updated:
Nov  5 00:06:32 BrandonsLinuxLaptop kernel: [  995.403888] cfg80211:  DFS Master region: unset
Nov  5 00:06:32 BrandonsLinuxLaptop kernel: [  995.403891] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Nov  5 00:06:32 BrandonsLinuxLaptop kernel: [  995.403898] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Nov  5 00:06:32 BrandonsLinuxLaptop kernel: [  995.403903] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Nov  5 00:06:32 BrandonsLinuxLaptop kernel: [  995.403908] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Nov  5 00:06:32 BrandonsLinuxLaptop kernel: [  995.403912] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Nov  5 00:06:32 BrandonsLinuxLaptop kernel: [  995.403917] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Nov  5 00:06:32 BrandonsLinuxLaptop NetworkManager[1125]: <info> (wlan0): cleaning up...
Nov  5 00:06:32 BrandonsLinuxLaptop NetworkManager[1125]: <info> (wlan0): taking down device.
Nov  5 00:06:32 BrandonsLinuxLaptop avahi-daemon[1064]: Interface wlan0.IPv6 no longer relevant for mDNS.
Nov  5 00:06:32 BrandonsLinuxLaptop avahi-daemon[1064]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::2acf:daff:fedf:5ec.
Nov  5 00:06:32 BrandonsLinuxLaptop avahi-daemon[1064]: Withdrawing address record for fe80::2acf:daff:fedf:5ec on wlan0.
Nov  5 00:06:32 BrandonsLinuxLaptop NetworkManager[1125]: <info> (/hfp/28CFDADF05ED_E4121D5E8072): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Nov  5 00:06:32 BrandonsLinuxLaptop NetworkManager[1125]: <info> (/hfp/28CFDADF05ED_E4121D5E8072): cleaning up...
Nov  5 00:06:32 BrandonsLinuxLaptop NetworkManager[1125]: <info> (/hfp/28CFDADF05ED_E4121D5E8072): taking down device.
Nov  5 00:06:32 BrandonsLinuxLaptop dbus[939]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov  5 00:06:32 BrandonsLinuxLaptop dbus[939]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Nov  5 00:06:32 BrandonsLinuxLaptop dbus[939]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov  5 00:06:32 BrandonsLinuxLaptop dbus[939]: [system] Successfully activated service 'org.freedesktop.systemd1'
Nov  5 00:06:32 BrandonsLinuxLaptop anacron[4836]: Anacron 2.3 started on 2014-11-05
Nov  5 00:06:32 BrandonsLinuxLaptop anacron[4836]: Will run job `cron.daily' in 5 min.
Nov  5 00:06:32 BrandonsLinuxLaptop anacron[4836]: Jobs will be executed sequentially
Nov  5 00:06:33 BrandonsLinuxLaptop kernel: [  996.251198] init: anacron main process (4836) killed by TERM signal
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: Deleting interface #7 wlan0, fe80::2acf:daff:fedf:5ec#123, interface stats: received=0, sent=0, dropped=0, active_time=931 secs
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: Deleting interface #6 wlan0, 2001:470:4:184:2acf:daff:fedf:5ec#123, interface stats: received=0, sent=0, dropped=0, active_time=931 secs
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: Deleting interface #5 wlan0, 2001:470:4:184:78e3:cacd:1e9c:4afb#123, interface stats: received=15, sent=15, dropped=0, active_time=931 secs
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: 2001:19f0:1590:5123:1057:a11:da7a:1 interface 2001:470:4:184:78e3:cacd:1e9c:4afb -> (none)
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: Deleting interface #3 wlan0, 192.168.1.124#123, interface stats: received=60, sent=60, dropped=0, active_time=931 secs
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: 91.189.94.4 interface 192.168.1.124 -> (none)
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: 69.64.45.119 interface 192.168.1.124 -> (none)
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: 96.44.142.5 interface 192.168.1.124 -> (none)
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: 108.61.56.35 interface 192.168.1.124 -> (none)
Nov  5 00:06:33 BrandonsLinuxLaptop ntpd[2086]: peers refreshed
Nov  5 00:06:34 BrandonsLinuxLaptop kernel: [  996.889351] PM: Syncing filesystems ... done.
Nov  5 00:06:34 BrandonsLinuxLaptop kernel: [  997.139526] PM: Preparing system for mem sleep
Nov  5 00:08:06 BrandonsLinuxLaptop rtkit-daemon[2548]: The canary thread is apparently starving. Taking action.
Nov  5 00:08:06 BrandonsLinuxLaptop rtkit-daemon[2548]: Demoting known real-time threads.
Nov  5 00:08:06 BrandonsLinuxLaptop rtkit-daemon[2548]: Successfully demoted thread 2897 of process 2544 (n/a).
Nov  5 00:08:06 BrandonsLinuxLaptop rtkit-daemon[2548]: Successfully demoted thread 2896 of process 2544 (n/a).
Nov  5 00:08:06 BrandonsLinuxLaptop rtkit-daemon[2548]: Successfully demoted thread 2544 of process 2544 (n/a).
Nov  5 00:08:06 BrandonsLinuxLaptop rtkit-daemon[2548]: Demoted 3 threads.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [  997.213528] Freezing user space processes ... (elapsed 0.001 seconds) done.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [  997.215069] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [  997.216157] PM: Entering mem sleep
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [  997.216179] Suspending console(s) (use no_console_suspend to debug)
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [  997.268626] sdhci: Timeout waiting for Buffer Read Ready interrupt during tuning procedure, falling back to fixed sampling clock
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1007.292808] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1007.344870] sdhci: Timeout waiting for Buffer Read Ready interrupt during tuning procedure, falling back to fixed sampling clock
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1007.354819] mmc0: Controller never released inhibit bit(s).
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1007.354866] mmc0: Unexpected interrupt 0x04000000.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1007.356254] apple-gmux 00:03: System wakeup disabled by ACPI
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1007.356471] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1007.373280] sd 0:0:0:0: [sda] Stopping disk
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1007.903050] [drm:rv770_stop_dpm] *ERROR* Could not force DPM to low.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.089016] PM: suspend of devices complete after 10872.559 msecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.089389] PM: late suspend of devices complete after 0.370 msecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.091210] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.092301] ehci-pci 0000:00:1a.7: System wakeup enabled by ACPI
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.092353] tg3 0000:02:00.0: System wakeup enabled by ACPI
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.104979] PM: noirq suspend of devices complete after 15.588 msecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.105227] ACPI: Preparing to enter system sleep state S3
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.105958] PM: Saving platform NVS memory
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.106122] Disabling non-boot CPUs ...
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.106167] intel_pstate CPU 1 exiting
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.107404] kvm: disabling virtualization on CPU1
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.208788] smpboot: CPU 1 is now offline
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.209073] intel_pstate CPU 2 exiting
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.210291] kvm: disabling virtualization on CPU2
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.312810] smpboot: CPU 2 is now offline
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.313095] intel_pstate CPU 3 exiting
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.314306] kvm: disabling virtualization on CPU3
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.416800] smpboot: CPU 3 is now offline
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.417098] intel_pstate CPU 4 exiting
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.418326] kvm: disabling virtualization on CPU4
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.520803] smpboot: CPU 4 is now offline
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.521067] intel_pstate CPU 5 exiting
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.522270] kvm: disabling virtualization on CPU5
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.624815] smpboot: CPU 5 is now offline
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.625062] intel_pstate CPU 6 exiting
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.625192] Broke affinity for irq 19
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.626225] kvm: disabling virtualization on CPU6
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.728799] smpboot: CPU 6 is now offline
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.729066] intel_pstate CPU 7 exiting
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.729248] Broke affinity for irq 23
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.730255] kvm: disabling virtualization on CPU7
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.832796] smpboot: CPU 7 is now offline
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.834331] ACPI: Low-level resume complete
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.834374] PM: Restoring platform NVS memory
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.834755] Enabling non-boot CPUs ...
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.834801] x86: Booting SMP configuration:
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.834802] smpboot: Booting Node 0 Processor 1 APIC 0x2
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.846172] kvm: enabling virtualization on CPU1
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.848499] Intel pstate controlling: cpu 1
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.848685] CPU1 is up
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.848704] smpboot: Booting Node 0 Processor 2 APIC 0x4
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.860173] kvm: enabling virtualization on CPU2
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.862448] Intel pstate controlling: cpu 2
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.862630] CPU2 is up
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.862652] smpboot: Booting Node 0 Processor 3 APIC 0x6
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.874158] kvm: enabling virtualization on CPU3
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.876461] Intel pstate controlling: cpu 3
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.876658] CPU3 is up
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.876677] smpboot: Booting Node 0 Processor 4 APIC 0x1
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.887823] kvm: enabling virtualization on CPU4
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.890048] Intel pstate controlling: cpu 4
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.890104] CPU4 is up
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.890124] smpboot: Booting Node 0 Processor 5 APIC 0x3
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.901624] kvm: enabling virtualization on CPU5
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.904014] Intel pstate controlling: cpu 5
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.904188] CPU5 is up
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.904209] smpboot: Booting Node 0 Processor 6 APIC 0x5
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.915600] kvm: enabling virtualization on CPU6
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.918073] Intel pstate controlling: cpu 6
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.918250] CPU6 is up
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.918271] smpboot: Booting Node 0 Processor 7 APIC 0x7
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.929770] kvm: enabling virtualization on CPU7
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.932278] Intel pstate controlling: cpu 7
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.932433] CPU7 is up
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1008.940858] ACPI: Waking up from system sleep state S3
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.827874] ehci-pci 0000:00:1a.7: System wakeup disabled by ACPI
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.827877] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.828990] PM: noirq resume of devices complete after 18.467 msecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.829279] PM: early resume of devices complete after 0.265 msecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.829344] mei_me 0000:00:16.0: irq 46 for MSI/MSI-X
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.829606] usb usb3: root hub lost power or was reset
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.829745] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.829914] usb usb4: root hub lost power or was reset
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.830071] snd_hda_intel 0000:01:00.1: irq 48 for MSI/MSI-X
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.830081] mei_me 0000:00:16.0: less data available than length=00000004.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.830145] tg3 0000:02:00.0: System wakeup disabled by ACPI
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.830543] sd 0:0:0:0: [sda] Starting disk
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.838012] [drm] PCIE gen 2 link speeds already enabled
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.842064] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.842155] radeon 0000:01:00.0: WB enabled
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.842157] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000c00 and cpu addr 0xffff88026265cc00
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.842159] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000010000c0c and cpu addr 0xffff88026265cc0c
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.855503] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc9000b732118
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.871759] [drm] ring test on 0 succeeded in 3 usecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1009.871770] [drm] ring test on 3 succeeded in 1 usecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.057618] [drm] ring test on 5 succeeded in 2 usecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.057625] [drm] UVD initialized successfully.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.057699] [drm] ib test on ring 0 succeeded in 0 usecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.057777] [drm] ib test on ring 3 succeeded in 1 usecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.209104] [drm] ib test on ring 5 succeeded
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214918] switching from power state:
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214920] 	ui class: none
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214921] 	internal class: boot 
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214922] 	caps: 
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214924] 	uvd    vclk: 0 dclk: 0
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214925] 		power level 0    sclk: 10000 mclk: 15000 vddc: 900 vddci: 0
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214926] 		power level 1    sclk: 10000 mclk: 15000 vddc: 900 vddci: 0
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214927] 		power level 2    sclk: 10000 mclk: 15000 vddc: 900 vddci: 0
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214928] 	status: c b 
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214928] switching to power state:
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214929] 	ui class: performance
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214929] 	internal class: none
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214930] 	caps: 
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214931] 	uvd    vclk: 0 dclk: 0
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214932] 		power level 0    sclk: 10000 mclk: 15000 vddc: 900 vddci: 0
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214932] 		power level 1    sclk: 40000 mclk: 79375 vddc: 1110 vddci: 0
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214933] 		power level 2    sclk: 75000 mclk: 79375 vddc: 1110 vddci: 0
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.214934] 	status: r 
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1010.382591] firewire_core 0000:04:00.0: rediscovered device fw0
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.178560] ata2.01: failed to resume link (SControl 0)
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.178665] ata1.01: failed to resume link (SControl 0)
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.334653] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.334667] ata2.01: SATA link down (SStatus 0 SControl 0)
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.334676] ata2.01: link offline, clearing class 3 to NONE
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.342828] ata2.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.358829] ata2.00: configured for UDMA/100
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.446654] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.446665] ata1.01: SATA link down (SStatus 0 SControl 0)
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.454825] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1011.470838] ata1.00: configured for UDMA/100
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1020.926684] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1030.942826] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1040.959003] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1050.975136] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1060.991301] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1071.007469] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1071.009625] mmc0: error -110 during resume (card was removed?)
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1071.009638] PM: resume of devices complete after 61179.417 msecs
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1071.010133] PM: Finishing wakeup.
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1071.010134] Restarting tasks ... 
Nov  5 00:08:06 BrandonsLinuxLaptop kernel: [ 1071.013163] done.
Nov  5 00:08:06 BrandonsLinuxLaptop anacron[5287]: Anacron 2.3 started on 2014-11-05
Nov  5 00:08:06 BrandonsLinuxLaptop anacron[5287]: Will run job `cron.daily' in 5 min.
Nov  5 00:08:06 BrandonsLinuxLaptop anacron[5287]: Jobs will be executed sequentially
Nov  5 00:08:16 BrandonsLinuxLaptop kernel: [ 1081.183617] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:26 BrandonsLinuxLaptop kernel: [ 1091.199751] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:36 BrandonsLinuxLaptop kernel: [ 1101.215934] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:46 BrandonsLinuxLaptop kernel: [ 1111.232090] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:08:46 BrandonsLinuxLaptop kernel: [ 1111.234249] mmc0: card 59b4 removed
Nov  5 00:08:56 BrandonsLinuxLaptop kernel: [ 1121.280260] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:09:06 BrandonsLinuxLaptop kernel: [ 1131.296422] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:09:16 BrandonsLinuxLaptop kernel: [ 1141.312600] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:09:26 BrandonsLinuxLaptop kernel: [ 1151.328755] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:09:36 BrandonsLinuxLaptop kernel: [ 1161.344922] mmc0: Timeout waiting for hardware interrupt.
Nov  5 00:09:46 BrandonsLinuxLaptop kernel: [ 1171.361078] mmc0: Timeout waiting for hardware interrupt.

```

---

