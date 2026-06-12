---
title: "Ubuntu won't go to sleep"
date: 2017-10-09
forum: General Help
---

### Post by t4ggs on 2017-10-09
Hi,

Any idea why I can't make my computer go to sleep/hibernate?

Each time I try it wakes up spontaneously after a few seconds.

See logs below:

```
Oct  9 20:58:02 ytagger-server org.gnome.Shell.desktop[2306]: Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3800084 (syslog (/v)
Oct  9 20:58:09 ytagger-server NetworkManager[760]: <info>  [1507571889.1162] manager: sleep requested (sleeping: no  enabled: yes)
Oct  9 20:58:09 ytagger-server NetworkManager[760]: <info>  [1507571889.1163] manager: sleeping...
Oct  9 20:58:09 ytagger-server NetworkManager[760]: <info>  [1507571889.1163] device (wlp2s0): state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Oct  9 20:58:09 ytagger-server NetworkManager[760]: <info>  [1507571889.1166] device (wlp2s0): set-hw-addr: reset MAC address to 30:B5:C2:46:1C:3A (unmanage)
Oct  9 20:58:09 ytagger-server NetworkManager[760]: <info>  [1507571889.1168] manager: NetworkManager state is now ASLEEP
Oct  9 20:58:09 ytagger-server dbus[742]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Oct  9 20:58:09 ytagger-server whoopsie[1223]: [20:58:09] offline
Oct  9 20:58:09 ytagger-server systemd[1]: Reached target Sleep.
Oct  9 20:58:09 ytagger-server systemd[1]: Starting Suspend...
Oct  9 20:58:09 ytagger-server systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct  9 20:58:09 ytagger-server dbus[742]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  9 20:58:09 ytagger-server nm-dispatcher: req:1 'connectivity-change': new request (1 scripts)
Oct  9 20:58:09 ytagger-server nm-dispatcher: req:1 'connectivity-change': start running ordered scripts...
Oct  9 20:58:09 ytagger-server systemd-sleep[9269]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Oct  9 20:58:09 ytagger-server systemd-sleep[9271]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Oct  9 20:58:09 ytagger-server systemd-sleep[9269]: Suspending system...
Oct  9 20:58:15 ytagger-server kernel: [ 7511.654816] PM: Syncing filesystems ... done.
Oct  9 20:58:15 ytagger-server kernel: [ 7511.665342] PM: Preparing system for sleep (mem)
Oct  9 20:58:15 ytagger-server kernel: [ 7511.665503] Freezing user space processes ... (elapsed 0.022 seconds) done.
Oct  9 20:58:15 ytagger-server kernel: [ 7511.688254] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Oct  9 20:58:15 ytagger-server kernel: [ 7511.689501] PM: Suspending system (mem)
Oct  9 20:58:15 ytagger-server kernel: [ 7511.689563] Suspending console(s) (use no_console_suspend to debug)
Oct  9 20:58:15 ytagger-server kernel: [ 7511.690636] sd 3:0:0:0: [sdb] Synchronizing SCSI cache
Oct  9 20:58:15 ytagger-server kernel: [ 7511.690772] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Oct  9 20:58:15 ytagger-server kernel: [ 7511.692752] sd 2:0:0:0: [sda] Stopping disk
Oct  9 20:58:15 ytagger-server kernel: [ 7511.692800] sd 3:0:0:0: [sdb] Stopping disk
Oct  9 20:58:15 ytagger-server kernel: [ 7511.693142] parport_pc 00:04: disabled
Oct  9 20:58:15 ytagger-server kernel: [ 7511.693264] serial 00:03: disabled
Oct  9 20:58:15 ytagger-server kernel: [ 7511.693270] serial 00:03: System wakeup disabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.224040] PM: suspend of devices complete after 534.208 msecs
Oct  9 20:58:15 ytagger-server kernel: [ 7512.244037] PM: late suspend of devices complete after 19.994 msecs
Oct  9 20:58:15 ytagger-server kernel: [ 7512.244325] pcieport 0000:00:1c.1: System wakeup enabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.244480] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.244543] uhci_hcd 0000:00:1d.3: System wakeup enabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.244567] uhci_hcd 0000:00:1d.2: System wakeup enabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.244589] uhci_hcd 0000:00:1d.1: System wakeup enabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.244613] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.264380] PM: noirq suspend of devices complete after 20.339 msecs
Oct  9 20:58:15 ytagger-server kernel: [ 7512.265187] ACPI: Preparing to enter system sleep state S3
Oct  9 20:58:15 ytagger-server kernel: [ 7512.341484] PM: Saving platform NVS memory
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342120] Disabling non-boot CPUs ...
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342497] Broke affinity for irq 1
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342504] Broke affinity for irq 8
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342507] Broke affinity for irq 9
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342510] Broke affinity for irq 12
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342520] Broke affinity for irq 16
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342527] Broke affinity for irq 19
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342530] Broke affinity for irq 23
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342534] Broke affinity for irq 25
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342535] Broke affinity for irq 26
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342536] Broke affinity for irq 27
Oct  9 20:58:15 ytagger-server kernel: [ 7512.342538] Broke affinity for irq 28
Oct  9 20:58:15 ytagger-server kernel: [ 7512.343576] smpboot: CPU 1 is now offline
Oct  9 20:58:15 ytagger-server kernel: [ 7512.352346] ACPI: Low-level resume complete
Oct  9 20:58:15 ytagger-server kernel: [ 7512.352346] PM: Restoring platform NVS memory
Oct  9 20:58:15 ytagger-server kernel: [ 7512.352346] Suspended for 4.152 seconds
Oct  9 20:58:15 ytagger-server kernel: [ 7512.357281] Enabling non-boot CPUs ...
Oct  9 20:58:15 ytagger-server kernel: [ 7512.368254] x86: Booting SMP configuration:
Oct  9 20:58:15 ytagger-server kernel: [ 7512.368255] smpboot: Booting Node 0 Processor 1 APIC 0x1
Oct  9 20:58:15 ytagger-server kernel: [ 7512.368997]  cache: parent cpu1 should not be sleeping
Oct  9 20:58:15 ytagger-server kernel: [ 7512.374004] CPU1 is up
Oct  9 20:58:15 ytagger-server kernel: [ 7512.376687] ACPI: Waking up from system sleep state S3
Oct  9 20:58:15 ytagger-server kernel: [ 7512.377413] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.377427] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.377457] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.377471] uhci_hcd 0000:00:1d.3: System wakeup disabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.396066] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.396307] PM: noirq resume of devices complete after 19.202 msecs
Oct  9 20:58:15 ytagger-server kernel: [ 7512.396325] pciehp 0000:00:1c.0:pcie004: Slot(0): Link Up
Oct  9 20:58:15 ytagger-server kernel: [ 7512.396335] pciehp 0000:00:1c.1:pcie004: Slot(0-1): Link Up
Oct  9 20:58:15 ytagger-server kernel: [ 7512.396455] PM: early resume of devices complete after 0.129 msecs
Oct  9 20:58:15 ytagger-server kernel: [ 7512.396612] usb usb2: root hub lost power or was reset
Oct  9 20:58:15 ytagger-server kernel: [ 7512.396641] usb usb3: root hub lost power or was reset
Oct  9 20:58:15 ytagger-server kernel: [ 7512.396668] usb usb4: root hub lost power or was reset
Oct  9 20:58:15 ytagger-server kernel: [ 7512.396695] usb usb5: root hub lost power or was reset
Oct  9 20:58:15 ytagger-server kernel: [ 7512.397269] ata2: port disabled--ignoring
Oct  9 20:58:15 ytagger-server kernel: [ 7512.399360] sd 2:0:0:0: [sda] Starting disk
Oct  9 20:58:15 ytagger-server kernel: [ 7512.399403] sd 3:0:0:0: [sdb] Starting disk
Oct  9 20:58:15 ytagger-server kernel: [ 7512.399823] serial 00:03: activated
Oct  9 20:58:15 ytagger-server kernel: [ 7512.400386] parport_pc 00:04: activated
Oct  9 20:58:15 ytagger-server kernel: [ 7512.400388] rtc_cmos 00:05: System wakeup disabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.404019] pciehp 0000:00:1c.1:pcie004: Timeout on hotplug command 0x1038 (issued 2874932 msec ago)
Oct  9 20:58:15 ytagger-server kernel: [ 7512.404026] pciehp 0000:00:1c.0:pcie004: Timeout on hotplug command 0x1038 (issued 2874932 msec ago)
Oct  9 20:58:15 ytagger-server kernel: [ 7512.504025] pciehp 0000:00:1c.1:pcie004: Device 0000:03:00.0 already exists at 0000:03:00, cannot hot-add
Oct  9 20:58:15 ytagger-server kernel: [ 7512.504027] pciehp 0000:00:1c.1:pcie004: Cannot add device at 0000:03:00
Oct  9 20:58:15 ytagger-server kernel: [ 7512.504044] pciehp 0000:00:1c.0:pcie004: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add
Oct  9 20:58:15 ytagger-server kernel: [ 7512.504045] pciehp 0000:00:1c.0:pcie004: Cannot add device at 0000:02:00
Oct  9 20:58:15 ytagger-server kernel: [ 7512.576131] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Oct  9 20:58:15 ytagger-server kernel: [ 7512.576134] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Oct  9 20:58:15 ytagger-server kernel: [ 7512.577569] ata3.00: ACPI cmd c6/00:01:00:00:00:a0 (SET MULTIPLE MODE) succeeded
Oct  9 20:58:15 ytagger-server kernel: [ 7512.577571] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Oct  9 20:58:15 ytagger-server kernel: [ 7512.612025] pciehp 0000:00:1c.1:pcie004: Device 0000:03:00.0 already exists at 0000:03:00, cannot hot-add
Oct  9 20:58:15 ytagger-server kernel: [ 7512.612027] pciehp 0000:00:1c.1:pcie004: Cannot add device at 0000:03:00
Oct  9 20:58:15 ytagger-server kernel: [ 7512.612044] pciehp 0000:00:1c.0:pcie004: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add
Oct  9 20:58:15 ytagger-server kernel: [ 7512.612046] pciehp 0000:00:1c.0:pcie004: Cannot add device at 0000:02:00
Oct  9 20:58:15 ytagger-server kernel: [ 7512.612060] pcieport 0000:00:1c.1: System wakeup disabled by ACPI
Oct  9 20:58:15 ytagger-server kernel: [ 7512.621567] ata3.00: configured for UDMA/133
Oct  9 20:58:15 ytagger-server kernel: [ 7512.677521] r8169 0000:03:00.0 enp3s0: link down
Oct  9 20:58:15 ytagger-server kernel: [ 7512.732032] usb 5-2: reset full-speed USB device number 4 using uhci_hcd
Oct  9 20:58:15 ytagger-server kernel: [ 7513.148027] usb 5-1: reset low-speed USB device number 5 using uhci_hcd
Oct  9 20:58:15 ytagger-server kernel: [ 7513.490860] PM: resume of devices complete after 1094.402 msecs
Oct  9 20:58:15 ytagger-server kernel: [ 7513.491086] PM: Finishing wakeup.
Oct  9 20:58:15 ytagger-server kernel: [ 7513.491087] Restarting tasks ... 
Oct  9 20:58:15 ytagger-server kernel: [ 7513.491127] pci 0000:00:1e.0: PCI bridge to [bus 04]
Oct  9 20:58:15 ytagger-server kernel: [ 7513.498514] pci 0000:00:1e.0: PCI bridge to [bus 04]
Oct  9 20:58:15 ytagger-server kernel: [ 7513.498560] pci 0000:00:1e.0: PCI bridge to [bus 04]
Oct  9 20:58:15 ytagger-server kernel: [ 7513.498600] pci 0000:00:1e.0: PCI bridge to [bus 04]
Oct  9 20:58:15 ytagger-server kernel: [ 7513.498639] pci 0000:00:1e.0: PCI bridge to [bus 04]
Oct  9 20:58:15 ytagger-server kernel: [ 7513.504712] done.
Oct  9 20:58:15 ytagger-server systemd[1376]: Time has been changed
Oct  9 20:58:15 ytagger-server systemd-sleep[9269]: System resumed.
Oct  9 20:58:15 ytagger-server systemd-sleep[9269]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Oct  9 20:58:15 ytagger-server systemd-sleep[9332]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Oct  9 20:58:15 ytagger-server systemd[1]: Time has been changed
Oct  9 20:58:15 ytagger-server systemd[1]: Started Network Manager Script Dispatcher Service.
Oct  9 20:58:15 ytagger-server systemd-sleep[9269]: /dev/sda:
Oct  9 20:58:15 ytagger-server systemd-sleep[9269]:  setting Advanced Power Management level to 0xfe (254)
Oct  9 20:58:15 ytagger-server systemd-sleep[9269]:  APM_level#011= 254
Oct  9 20:58:15 ytagger-server chromium-browser.desktop[3296]: [3296:3331:1009/205815.650556:ERROR:connection_factory_impl.cc(386)] Failed to connect to MCS endpoint with error -106
Oct  9 20:58:16 ytagger-server kernel: [ 7515.223485] r8169 0000:03:00.0 enp3s0: link up
Oct  9 20:58:16 ytagger-server NetworkManager[760]: <info>  [1507571896.8719] device (enp3s0): link connected
Oct  9 20:58:16 ytagger-server NetworkManager[760]: <info>  [1507571896.8730] device (enp3s0): DHCPv4 lease renewal requested
Oct  9 20:58:16 ytagger-server NetworkManager[760]: <info>  [1507571896.9052] dhcp4 (enp3s0): canceled DHCP transaction, DHCP client pid 8777
Oct  9 20:58:16 ytagger-server NetworkManager[760]: <info>  [1507571896.9053] dhcp4 (enp3s0): state changed bound -> done
Oct  9 20:58:16 ytagger-server NetworkManager[760]: <info>  [1507571896.9057] dhcp4 (enp3s0): activation: beginning transaction (timeout in 45 seconds)
Oct  9 20:58:16 ytagger-server NetworkManager[760]: <info>  [1507571896.9092] dhcp4 (enp3s0): dhclient started with pid 9368
Oct  9 20:58:16 ytagger-server dhclient[9368]: DHCPREQUEST of 192.168.1.6 on enp3s0 to 255.255.255.255 port 67 (xid=0x1731cca1)
Oct  9 20:58:19 ytagger-server kernel: [ 7517.452019] ata4: link is slow to respond, please be patient (ready=0)
Oct  9 20:58:19 ytagger-server org.gnome.Shell.desktop[2306]: Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3800084 (*syslog (/)
```

Thanks

---

### Post by t4ggs on 2017-10-14
Bump

---

