---
title: "Suspend not working -  help needed to debug"
date: 2017-12-19
forum: General Help
---

### Post by kapad on 2017-12-19
Since the past couple of days, each time I try to suspend my system, my laptop immediately resumes from suspend. I'm not sure what the exact error is. 

I also noticed, that since this problem began, there's been no messages logged to /var/log/pm-suspend.log

Also, I cannot really decipher the syslog and figure out what the issue is. 
I've copied in the relevant portions of my syslog below (atleast what I thought was relevant. If there is something else that I should add to the syslog dump, or any other log files that I need to add to the post, please let me know).

```

Dec 19 19:43:42 rocket systemd[1]: Starting Suspend...
Dec 19 19:43:42 rocket systemd-sleep[14238]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Dec 19 19:43:42 rocket systemd-sleep[14245]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Dec 19 19:43:42 rocket systemd-sleep[14238]: Suspending system...
Dec 19 19:43:42 rocket kernel: [97753.657438] PM: suspend entry (deep)
Dec 19 19:43:49 rocket kernel: [97753.657440] PM: Syncing filesystems ... done.
Dec 19 19:43:49 rocket kernel: [97753.677370] Freezing user space processes ... (elapsed 0.002 seconds) done.
Dec 19 19:43:49 rocket kernel: [97753.679487] OOM killer disabled.
Dec 19 19:43:49 rocket kernel: [97753.679487] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Dec 19 19:43:49 rocket kernel: [97753.681041] Suspending console(s) (use no_console_suspend to debug)
Dec 19 19:43:49 rocket kernel: [97753.694559] e1000e: EEE TX LPI TIMER: 00000011
Dec 19 19:43:49 rocket kernel: [97754.015324] ACPI: Preparing to enter system sleep state S3
Dec 19 19:43:49 rocket kernel: [97754.058898] ACPI: EC: event blocked
Dec 19 19:43:49 rocket kernel: [97754.058899] ACPI: EC: EC stopped
Dec 19 19:43:49 rocket kernel: [97754.058901] PM: Saving platform NVS memory
Dec 19 19:43:49 rocket kernel: [97754.059053] Disabling non-boot CPUs ...
Dec 19 19:43:49 rocket kernel: [97754.075214] irq_migrate_all_off_this_cpu: 1 callbacks suppressed
Dec 19 19:43:49 rocket kernel: [97754.075217] IRQ 127: no longer affine to CPU1
Dec 19 19:43:49 rocket kernel: [97754.076265] smpboot: CPU 1 is now offline
Dec 19 19:43:49 rocket kernel: [97754.099125] IRQ 122: no longer affine to CPU2
Dec 19 19:43:49 rocket kernel: [97754.099135] IRQ 123: no longer affine to CPU2
Dec 19 19:43:49 rocket kernel: [97754.099152] IRQ 129: no longer affine to CPU2
Dec 19 19:43:49 rocket kernel: [97754.099161] IRQ 133: no longer affine to CPU2
Dec 19 19:43:49 rocket kernel: [97754.101239] smpboot: CPU 2 is now offline
Dec 19 19:43:49 rocket kernel: [97754.127042] IRQ 1: no longer affine to CPU3
Dec 19 19:43:49 rocket kernel: [97754.127053] IRQ 8: no longer affine to CPU3
Dec 19 19:43:49 rocket kernel: [97754.127061] IRQ 9: no longer affine to CPU3
Dec 19 19:43:49 rocket kernel: [97754.127070] IRQ 12: no longer affine to CPU3
Dec 19 19:43:49 rocket kernel: [97754.127092] IRQ 124: no longer affine to CPU3
Dec 19 19:43:49 rocket kernel: [97754.128146] smpboot: CPU 3 is now offline
Dec 19 19:43:49 rocket kernel: [97754.134445] ACPI: Low-level resume complete
Dec 19 19:43:49 rocket kernel: [97754.134553] ACPI: EC: EC started
Dec 19 19:43:49 rocket kernel: [97754.134554] PM: Restoring platform NVS memory
Dec 19 19:43:49 rocket kernel: [97754.136858] Enabling non-boot CPUs ...
Dec 19 19:43:49 rocket kernel: [97754.136960] x86: Booting SMP configuration:
Dec 19 19:43:49 rocket kernel: [97754.136961] smpboot: Booting Node 0 Processor 1 APIC 0x2
Dec 19 19:43:49 rocket kernel: [97754.138995]  cache: parent cpu1 should not be sleeping
Dec 19 19:43:49 rocket kernel: [97754.139198] CPU1 is up
Dec 19 19:43:49 rocket kernel: [97754.139220] smpboot: Booting Node 0 Processor 2 APIC 0x1
Dec 19 19:43:49 rocket kernel: [97754.140866]  cache: parent cpu2 should not be sleeping
Dec 19 19:43:49 rocket kernel: [97754.141062] CPU2 is up
Dec 19 19:43:49 rocket kernel: [97754.141089] smpboot: Booting Node 0 Processor 3 APIC 0x3
Dec 19 19:43:49 rocket kernel: [97754.142607]  cache: parent cpu3 should not be sleeping
Dec 19 19:43:49 rocket kernel: [97754.142810] CPU3 is up
Dec 19 19:43:49 rocket kernel: [97754.145878] ACPI: Waking up from system sleep state S3
Dec 19 19:43:49 rocket kernel: [97754.840298] ACPI: EC: event unblocked
Dec 19 19:43:49 rocket kernel: [97755.373360] ata1: SATA link down (SStatus 4 SControl 300)
Dec 19 19:43:49 rocket kernel: [97755.373390] ata2: SATA link down (SStatus 0 SControl 300)
Dec 19 19:43:49 rocket kernel: [97755.394993] usb 1-2: reset high-speed USB device number 2 using xhci_hcd
Dec 19 19:43:49 rocket kernel: [97755.563924] restoring control 00000000-0000-0000-0000-000000000101/10/5
Dec 19 19:43:49 rocket kernel: [97755.563928] restoring control 00000000-0000-0000-0000-000000000101/12/11
Dec 19 19:43:49 rocket kernel: [97755.670949] usb 1-4: reset high-speed USB device number 37 using xhci_hcd
Dec 19 19:43:49 rocket kernel: [97756.115174] usb 1-4.1: reset full-speed USB device number 38 using xhci_hcd
Dec 19 19:43:49 rocket kernel: [97756.295223] usb 1-4.2: reset full-speed USB device number 39 using xhci_hcd
Dec 19 19:43:49 rocket kernel: [97756.471198] OOM killer enabled.
Dec 19 19:43:49 rocket systemd[1]: Time has been changed
Dec 19 19:43:49 rocket systemd[3214]: Time has been changed
Dec 19 19:43:49 rocket kernel: [97756.471201] Restarting tasks ... 
Dec 19 19:43:49 rocket kernel: [97756.477635] [drm] RC6 on
Dec 19 19:43:49 rocket kernel: [97756.479382] done.
Dec 19 19:43:49 rocket kernel: [97756.509711] acpi PNP0401:00: Already enumerated
Dec 19 19:43:49 rocket compiz[3686]: WARN  2017-12-19 19:43:49 unity.glib.dbus.proxy GLibDBusProxy.cpp:487 Calling method "EmitEvent" on object path: "/com/ubuntu/Upstart" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name com.canonical.Unity.Test.Upstart was not provided by any .service files
Dec 19 19:43:49 rocket systemd[1]: Reloading Laptop Mode Tools.
Dec 19 19:43:49 rocket kernel: [97756.599394] acpi PNP0501:00: Still not present
Dec 19 19:43:49 rocket laptop_mode[14272]: Laptop mode
Dec 19 19:43:49 rocket laptop_mode[14272]: enabled, not active [unchanged]
Dec 19 19:43:49 rocket systemd-sleep[14238]: System resumed.
Dec 19 19:43:49 rocket kernel: [97756.656991] PM: suspend exit
Dec 19 19:43:49 rocket systemd-sleep[14238]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Dec 19 19:43:49 rocket systemd-sleep[14317]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Dec 19 19:43:49 rocket systemd[1]: Started Suspend.
Dec 19 19:43:49 rocket systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Dec 19 19:43:49 rocket systemd[1]: Stopped target Sleep.
Dec 19 19:43:49 rocket systemd[1]: Reached target Suspend.
Dec 19 19:43:49 rocket systemd[1]: suspend.target: Unit is bound to inactive unit systemd-suspend.service. Stopping, too.
Dec 19 19:43:49 rocket systemd[1]: Stopped target Suspend.
Dec 19 19:43:49 rocket systemd[1]: Started Run anacron jobs at resume.

```

---

### Post by TheFu on 2017-12-19
Which release?  17.04 support ends in a few weeks, so moving to 17.10 would be the first step before wasting much time on a soon-to-be-DoA release.

I can't find why I thought you were running 17.04 now - was it in the tags for this post?  Your signature still says 10.04, so that isn't it. ;)

It appears that wifi might not be cooperating.  If you manually turn off wifi, does the suspend work?

---

### Post by kapad on 2017-12-19
Technically, 17.04 support has already ended. Bu I'm still on 17.04 right now.

---

