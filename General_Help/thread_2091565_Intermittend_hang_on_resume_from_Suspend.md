---
title: "Intermittend hang on resume from Suspend"
date: 2012-12-05
forum: General Help
---

### Post by hartz on 2012-12-05
Good day.

I am running kubuntu 12.10 with most updates installed (I just noticed there are more updates since yesterday).

Every now and then (about 33% of the time, I would estimate) my laptop freezes on resuming.

My primary suspect is either graphics hardware or VirtualBox.  I had no problems with Kubuntu 12.04 on my previous laptop, a venerable Lenovo T61.

My current laptop is an HP ProBook 6560b with
Intel i5-2410M CPU and 8 GB ram.

```

# lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at d4000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [a4] PCI Advanced Features
        Kernel driver in use: i915
        Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, fast devsel, latency 0, IRQ 47
        Memory at d4724000 (64-bit, non-prefetchable) [size=16]
        Capabilities: [50] Power Management version 3
        Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Kernel driver in use: mei
        Kernel modules: mei

00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: fast devsel, IRQ 20
        Memory at d4700000 (32-bit, non-prefetchable) [disabled] [size=128K]
        Memory at d472a000 (32-bit, non-prefetchable) [disabled] [size=4K]
        I/O ports at 4060 [disabled] [size=32]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [e0] PCI Advanced Features
        Kernel driver in use: e1000e
        Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at d4729000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCI Advanced Features
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at d4720000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Root Complex Link
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: d4600000-d46fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Device 1619
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=22, sec-latency=0
        I/O behind bridge: 00002000-00003fff
        Memory behind bridge: d0000000-d3ffffff
        Prefetchable memory behind bridge: 00000000bfb00000-00000000bfcfffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Device 1619
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=23, subordinate=23, sec-latency=0
        Memory behind bridge: d4500000-d45fffff
        Prefetchable memory behind bridge: 00000000bfd00000-00000000bfdfffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Device 1619
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=24, subordinate=24, sec-latency=0
        Memory behind bridge: d4400000-d44fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Device 1619
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at d4728000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCI Advanced Features
        Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
        I/O ports at 4088 [size=8]
        I/O ports at 4094 [size=4]
        I/O ports at 4080 [size=8]
        I/O ports at 4090 [size=4]
        I/O ports at 4040 [size=32]
        Memory at d4727000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] SATA HBA v1.0
        Capabilities: [b0] PCI Advanced Features
        Kernel driver in use: ahci

23:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d4500000 (32-bit, non-prefetchable) [size=2K]
        Memory at d4505000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Power Management version 3
        Capabilities: [80] Express Endpoint, MSI 00
        Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
        Kernel driver in use: firewire_ohci
        Kernel modules: firewire-ohci

23:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d4504000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at bfd00000 [disabled] [size=32K]
        Capabilities: [a4] Power Management version 3
        Capabilities: [80] Express Endpoint, MSI 00
        Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

23:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30) (prog-if 01)
        Subsystem: Hewlett-Packard Company Device 1619
        Flags: fast devsel, IRQ 18
        Memory at d4503000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [a4] Power Management version 3
        Capabilities: [80] Express Endpoint, MSI 00
        Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
        Kernel modules: sdhci-pci

24:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
        Subsystem: Hewlett-Packard Company Device 145c
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information: Len=78 <?>
        Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [160] Device Serial Number 00-00-12-ff-ff-c8-ac-81
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: wl
        Kernel modules: wl, bcma

```

I'm hoping someone have some hints about where I should start looking to solve this.  Also I am going to close my VirtualBoxes before I suspend for a while and see if that makes any difference.

Cheers,
  _Johan

---

### Post by hartz on 2012-12-05
I have been looking though the logs in /var/log.

I can see the last suspend process recorded in several logs (syslog, kern.log, etc) ending at around 15:16.

I "resumed" at about 16:30 and got the desktop to display, which is as expected, but then a hard hang - no mouse movement, can not toggle num-lock-and-friends, etc.  After hard rebooting (10 seconds on the power button) the system came back up and looks normal, with my open windows restored, etc.  But there is nothing in any of the log files between the last suspend messages and the first new bootup messages at about 16:39.

Is there some more kernel or power-management related logging that I can enabled somewhere to debug this?

Snippet from /var/log/syslog
```

Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ NetworkManager[1181]: <info> (eth1): now unmanaged
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ NetworkManager[1181]: <info> (eth1): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ NetworkManager[1181]: <info> (eth1): cleaning up...
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ NetworkManager[1181]: <info> (eth1): taking down device.
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ avahi-daemon[1227]: Interface eth1.IPv6 no longer relevant for mDNS.
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ avahi-daemon[1227]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::ae81:12ff:fec8:e1fb.
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ avahi-daemon[1227]: Withdrawing address record for fe80::ae81:12ff:fec8:e1fb on eth1.
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ NetworkManager[1181]: <info> (usb0): now unmanaged
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ NetworkManager[1181]: <info> (usb0): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ NetworkManager[1181]: <info> (usb0): cleaning up...
Dec  5 15:16:30 johan-HP-ProBook-6560b-LG654EA-ACQ anacron[7757]: Anacron 2.3 started on 2012-12-05
Dec  5 15:16:30 johan-HP-ProBook-6560b-LG654EA-ACQ anacron[7757]: Normal exit (0 jobs run)
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1122" x-info="http://www.rsyslog.com"] start
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ rsyslogd: rsyslogd's groupid changed to 103
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ rsyslogd: rsyslogd's userid changed to 101
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] Linux version 3.5.0-19-generic (buildd@komainu) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 (Ubuntu 3.5.0-19.30-generic 3.5.7)
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-19-generic root=UUID=6868f728-c6de-4c4f-9f81-a2834f47cddb ro quiet splash vt.handoff=7
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] KERNEL supported cpus:
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000]   Intel GenuineIntel
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000]   AMD AuthenticAMD
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000]   Centaur CentaurHauls
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bc4dcfff] usable
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000bc4dd000-0x00000000bccdcfff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000bccdd000-0x00000000bcf5cfff] ACPI NVS
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000bcf5d000-0x00000000bcffefff] ACPI data
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000bcfff000-0x00000000bcffffff] usable
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000bd000000-0x00000000bf9fffff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved

```

Snippet from kern.log
```

Dec  5 10:49:14 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [ 3272.786160] hp_wmi: Unknown event_id - 8 - 0x1
Dec  5 10:55:25 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [ 3643.645138] hp_wmi: Unknown event_id - 8 - 0x2
Dec  5 11:10:20 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [ 4537.602350] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Dec  5 11:10:36 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [ 4553.637639] EXT4-fs (sda6): Unaligned AIO/DIO on inode 1966082 by AioMgr0-N; performance will be poor.
Dec  5 11:45:31 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [ 6647.977434] hp_wmi: Unknown event_id - 8 - 0x1
Dec  5 12:17:16 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [ 8551.587512] hp_wmi: Unknown event_id - 8 - 0x2
Dec  5 14:16:46 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [15718.014395] hp_wmi: Unknown event_id - 8 - 0x1
Dec  5 14:30:42 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [16553.784932] hp_wmi: Unknown event_id - 8 - 0x2
Dec  5 15:15:54 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [19264.181616] hp_wmi: Unknown event_id - 8 - 0x1
Dec  5 15:16:29 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [19299.103639] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] Linux version 3.5.0-19-generic (buildd@komainu) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 (Ubuntu 3.5.0-19.30-generic 3.5.7)
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-19-generic root=UUID=6868f728-c6de-4c4f-9f81-a2834f47cddb ro quiet splash vt.handoff=7
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] KERNEL supported cpus:
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000]   Intel GenuineIntel
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000]   AMD AuthenticAMD
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000]   Centaur CentaurHauls
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bc4dcfff] usable
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000bc4dd000-0x00000000bccdcfff] reserved
Dec  5 16:39:34 johan-HP-ProBook-6560b-LG654EA-ACQ kernel: [    0.000000] BIOS-e820: [mem 0x00000000bccdd000-0x00000000bcf5cfff] ACPI NVS

```

Thank you!

---

### Post by hartz on 2012-12-05
Hmmmm.... I just found this: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) ... looks promising....

---

### Post by 2F4U on 2012-12-05
There is a log file dedicated to actions which take place during suspend/resume: 

/var/log/pm-suspend.log

[http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html)

---

