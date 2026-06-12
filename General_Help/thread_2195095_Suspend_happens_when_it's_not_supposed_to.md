---
title: "Suspend happens when it's not supposed to?"
date: 2013-12-22
forum: General Help
---

### Post by PaulBx on 2013-12-22
Lenovo G780 running Lubuntu 13.10.

I was doing a "tail" of /var/log/messages last night (Dec 21), and around 11pm closed the cover (I have xfce power manager set to "lock screen" when lid is closed and "put computer to sleep when inactive" at "never"). This morning I opened it up and noticed the tail messages where it went into a suspend cycle just as I opened the lid, immediately followed by a resume. Seems like it shouldn't be suspending at all in that circumstance:

```

Dec 21 08:37:55 len780 kernel: [ 2410.972199] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
Dec 21 21:31:16 len780 kernel: [48841.330617] perf samples too long (2511 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Dec 22 07:34:54 len780 kernel: [54875.956406] PM: Syncing filesystems ... done.
Dec 22 07:34:54 len780 kernel: [54875.958374] Freezing user space processes ... (elapsed 0.001 seconds) done.
Dec 22 07:34:54 len780 kernel: [54875.959519] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Dec 22 07:34:54 len780 kernel: [54875.960716] Suspending console(s) (use no_console_suspend to debug)
Dec 22 07:34:54 len780 kernel: [54875.960957] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Dec 22 07:34:54 len780 kernel: [54875.962244] sd 0:0:0:0: [sda] Stopping disk
Dec 22 07:34:54 len780 kernel: [54876.417020] PM: suspend of devices complete after 455.920 msecs
Dec 22 07:34:54 len780 kernel: [54876.417151] PM: late suspend of devices complete after 0.128 msecs
Dec 22 07:34:54 len780 kernel: [54876.433377] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
Dec 22 07:34:54 len780 kernel: [54876.449052] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
Dec 22 07:34:54 len780 kernel: [54876.480977] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
Dec 22 07:34:54 len780 kernel: [54876.496981] PM: noirq suspend of devices complete after 79.778 msecs
Dec 22 07:34:54 len780 kernel: [54876.497160] ACPI: Preparing to enter system sleep state S3
Dec 22 07:34:54 len780 kernel: [54876.497310] PM: Saving platform NVS memory
Dec 22 07:34:54 len780 kernel: [54876.497860] Disabling non-boot CPUs ...
Dec 22 07:34:54 len780 kernel: [54876.601034] smpboot: CPU 1 is now offline
Dec 22 07:34:54 len780 kernel: [54876.705100] smpboot: CPU 2 is now offline
Dec 22 07:34:54 len780 kernel: [54876.705453] Broke affinity for irq 17
Dec 22 07:34:54 len780 kernel: [54876.705462] Broke affinity for irq 23
Dec 22 07:34:54 len780 kernel: [54876.809158] smpboot: CPU 3 is now offline
Dec 22 07:34:54 len780 kernel: [54876.810232] ACPI: Low-level resume complete
Dec 22 07:34:54 len780 kernel: [54876.810277] PM: Restoring platform NVS memory
Dec 22 07:34:54 len780 kernel: [54876.810759] Enabling non-boot CPUs ...
Dec 22 07:34:54 len780 kernel: [54876.810791] smpboot: Booting Node 0 Processor 1 APIC 0x1
Dec 22 07:34:54 len780 kernel: [54876.840667] CPU1 is up
Dec 22 07:34:54 len780 kernel: [54876.840682] smpboot: Booting Node 0 Processor 2 APIC 0x2
Dec 22 07:34:54 len780 kernel: [54876.854289] CPU2 is up
Dec 22 07:34:54 len780 kernel: [54876.854304] smpboot: Booting Node 0 Processor 3 APIC 0x3
Dec 22 07:34:54 len780 kernel: [54876.868045] CPU3 is up
Dec 22 07:34:54 len780 kernel: [54876.871050] ACPI: Waking up from system sleep state S3
.
.
.

```

I am going to try telling it to suspend or hibernate on closing the lid, but I thought I ought to mention the above...

---

### Post by Toz on 2013-12-22
Looks like [this bug]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021"). Workaround is to disable systemd lid handling - see post #5 in that bug report. There also now seems to be a PPA for a patched version of the xfce4 power manager available.

---

