---
title: "Ubuntu wakes up from suspend after 25 min by itself"
date: 2018-04-03
forum: General Help
---

### Post by docdoc2 on 2018-04-03
Hello,

my battery was very low so i suspended the laptop. after 25min, without any apparent reason, the laptop woke up from suspend. 

This seems to happen only when the battery is low, but according to the syslog, the problem is the network manager: [I]NetworkManager[1176]: Apr  3 20:49:03 FRDL NetworkManager[1176]: <info>  [1522781343.1365] manager: **wake requested** (sleeping: yes  enabled: yes)

[/I]Or could it be something else? How can i prevent anything from waking up the laptop except an user input? It is dangerous if the computer suddenly wakes up during transport as it could damage the hdd.

```
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.3755] manager: sleep requested (sleeping: no  enabled: yes)
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.3756] manager: sleeping...
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.3759] manager: NetworkManager state is now ASLEEP
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.3767] device (wlo1): state change: activated -> deactivating (reason 'sleeping') [100 110 37]
Apr  3 20:21:53 FRDL whoopsie[1797]: [20:21:53] offline
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.3846] device (wlo1): state change: deactivating -> disconnected (reason 'sleeping') [110 30 37]
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Withdrawing address record for 2003:d1:43ca:8000:2cda:f2d5:6d57:442c on wlo1.
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Withdrawing address record for 2003:d1:43ca:8000:467d:b994:4361:d815 on wlo1.
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Leaving mDNS multicast group on interface wlo1.IPv6 with address 2003:d1:43ca:8000:467d:b994:4361:d815.
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Joining mDNS multicast group on interface wlo1.IPv6 with address fe80::3945:666c:4a24:3dd1.
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Registering new address record for fe80::3945:666c:4a24:3dd1 on wlo1.*.
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Withdrawing address record for fe80::3945:666c:4a24:3dd1 on wlo1.
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Leaving mDNS multicast group on interface wlo1.IPv6 with address fe80::3945:666c:4a24:3dd1.
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Interface wlo1.IPv6 no longer relevant for mDNS.
Apr  3 20:21:53 FRDL org.gtk.vfs.Daemon[2026]: ** (process:2732): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.4191] dhcp4 (wlo1): canceled DHCP transaction, DHCP client pid 23435
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.4192] dhcp4 (wlo1): state changed bound -> done
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.4201] dhcp6 (wlo1): canceled DHCP transaction
Apr  3 20:21:53 FRDL kernel: [63991.475643] wlo1: deauthenticating from 80:2a:a8:c1:3d:70 by local choice (Reason: 3=DEAUTH_LEAVING)
Apr  3 20:21:53 FRDL wpa_supplicant[1418]: wlo1: CTRL-EVENT-DISCONNECTED bssid=80:2a:a8:c1:3d:70 reason=3 locally_generated=1
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Withdrawing address record for 192.168.179.178 on wlo1.
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Leaving mDNS multicast group on interface wlo1.IPv4 with address 192.168.179.178.
Apr  3 20:21:53 FRDL avahi-daemon[1100]: Interface wlo1.IPv4 no longer relevant for mDNS.
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.4490] dns-mgr: Writing DNS information to /sbin/resolvconf
Apr  3 20:21:53 FRDL dnsmasq[1501]: setting upstream servers from DBus
Apr  3 20:21:53 FRDL dnsmasq[1501]: using nameserver fd00::9ec7:a6ff:fe11:9a71#53(via wlo1)
Apr  3 20:21:53 FRDL wpa_supplicant[1418]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Apr  3 20:21:53 FRDL org.gtk.vfs.Daemon[2026]: ** (process:2732): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Apr  3 20:21:53 FRDL dnsmasq[1317]: reading /var/run/dnsmasq/resolv.conf
Apr  3 20:21:53 FRDL dnsmasq[1317]: using nameserver 127.0.1.1#53
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.5201] dns-mgr: Writing DNS information to /sbin/resolvconf
Apr  3 20:21:53 FRDL dnsmasq[1501]: setting upstream servers from DBus
Apr  3 20:21:53 FRDL NetworkManager[1176]: <warn>  [1522779713.5307] sup-iface[0x1bde0c0,wlo1]: connection disconnected (reason -3)
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.5309] device (wlo1): supplicant interface state: completed -> disconnected
Apr  3 20:21:53 FRDL nm-dispatcher: req:3 'down' [wlo1]: new request (1 scripts)
Apr  3 20:21:53 FRDL nm-dispatcher: req:3 'down' [wlo1]: start running ordered scripts...
Apr  3 20:21:53 FRDL NetworkManager[1176]: <info>  [1522779713.5316] device (wlo1): state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Apr  3 20:21:54 FRDL systemd[1]: Reached target Sleep.
Apr  3 20:21:54 FRDL systemd[1]: Starting Suspend...
Apr  3 20:21:54 FRDL wpa_supplicant[1418]: nl80211: deinit ifname=wlo1 disabled_11b_rates=0
Apr  3 20:22:03 FRDL kernel: [64001.832864] pci_bus 0000:07: Allocating resources
Apr  3 20:22:03 FRDL kernel: [64001.832892] pci_bus 0000:08: Allocating resources
Apr  3 20:22:03 FRDL kernel: [64001.832949] pci_bus 0000:0a: Allocating resources
Apr  3 20:22:03 FRDL kernel: [64001.833003] pci_bus 0000:0b: Allocating resources
Apr  3 20:22:03 FRDL kernel: [64001.833255] pci_bus 0000:01: Allocating resources
Apr  3 20:22:04 FRDL systemd-sleep[23677]: Selected interface 'wlo1'
Apr  3 20:22:04 FRDL systemd-sleep[23677]: 'SUSPEND' command timed out.
Apr  3 20:22:04 FRDL systemd-sleep[23678]: /lib/systemd/system-sleep/wpasupplicant failed with error code 254.
Apr  3 20:22:04 FRDL systemd-sleep[23677]: Suspending system...
Apr  3 20:22:04 FRDL kernel: [64002.121836] PM: Syncing filesystems ... done.
Apr  3 20:22:04 FRDL kernel: [64002.241169] PM: Preparing system for sleep (mem)
Apr  3 20:48:59 FRDL kernel: [64002.753553] Freezing user space processes ... (elapsed 0.002 seconds) done.
Apr  3 20:48:59 FRDL kernel: [64002.756360] OOM killer disabled.
Apr  3 20:48:59 FRDL kernel: [64002.756361] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Apr  3 20:48:59 FRDL kernel: [64002.757898] PM: Suspending system (mem)
Apr  3 20:48:59 FRDL kernel: [64002.757937] Suspending console(s) (use no_console_suspend to debug)
Apr  3 20:48:59 FRDL kernel: [64002.758567] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Apr  3 20:48:59 FRDL kernel: [64002.798439] sd 0:0:0:0: [sda] Stopping disk
Apr  3 20:48:59 FRDL kernel: [64003.424753] PM: suspend of devices complete after 666.571 msecs
Apr  3 20:48:59 FRDL kernel: [64003.444571] PM: late suspend of devices complete after 19.799 msecs
Apr  3 20:48:59 FRDL kernel: [64003.524461] PM: noirq suspend of devices complete after 79.884 msecs
Apr  3 20:48:59 FRDL kernel: [64003.524965] ACPI: Preparing to enter system sleep state S3
Apr  3 20:48:59 FRDL kernel: [64003.604521] ACPI: EC: event blocked
Apr  3 20:48:59 FRDL kernel: [64003.604522] ACPI: EC: EC stopped
Apr  3 20:48:59 FRDL kernel: [64003.604523] PM: Saving platform NVS memory
Apr  3 20:48:59 FRDL kernel: [64003.604542] Disabling non-boot CPUs ...
Apr  3 20:48:59 FRDL kernel: [64003.621115] IRQ 27: no longer affine to CPU1
Apr  3 20:48:59 FRDL kernel: [64003.621119] IRQ 30: no longer affine to CPU1
Apr  3 20:48:59 FRDL kernel: [64003.622130] smpboot: CPU 1 is now offline
Apr  3 20:48:59 FRDL kernel: [64003.645878] smpboot: CPU 2 is now offline
Apr  3 20:48:59 FRDL kernel: [64003.669023] IRQ 24: no longer affine to CPU3
Apr  3 20:48:59 FRDL kernel: [64003.670044] smpboot: CPU 3 is now offline
Apr  3 20:48:59 FRDL kernel: [64003.701958] smpboot: CPU 4 is now offline
Apr  3 20:48:59 FRDL kernel: [64003.724922] IRQ 32: no longer affine to CPU5
Apr  3 20:48:59 FRDL kernel: [64003.725934] smpboot: CPU 5 is now offline
Apr  3 20:48:59 FRDL kernel: [64003.750034] smpboot: CPU 6 is now offline
Apr  3 20:48:59 FRDL kernel: [64003.772840] IRQ 1: no longer affine to CPU7
Apr  3 20:48:59 FRDL kernel: [64003.772844] IRQ 9: no longer affine to CPU7
Apr  3 20:48:59 FRDL kernel: [64003.772851] IRQ 12: no longer affine to CPU7
Apr  3 20:48:59 FRDL kernel: [64003.772863] IRQ 28: no longer affine to CPU7
Apr  3 20:48:59 FRDL kernel: [64003.773878] smpboot: CPU 7 is now offline
Apr  3 20:48:59 FRDL kernel: [64003.775523] ACPI: Low-level resume complete
Apr  3 20:48:59 FRDL kernel: [64003.775581] ACPI: EC: EC started
Apr  3 20:48:59 FRDL kernel: [64003.775581] PM: Restoring platform NVS memory
Apr  3 20:48:59 FRDL kernel: [64003.775905] Suspended for 1612.279 seconds
Apr  3 20:48:59 FRDL kernel: [64003.781156] Enabling non-boot CPUs ...
Apr  3 20:48:59 FRDL kernel: [64003.781216] x86: Booting SMP configuration:
Apr  3 20:48:59 FRDL kernel: [64003.781217] smpboot: Booting Node 0 Processor 1 APIC 0x1
Apr  3 20:48:59 FRDL kernel: [64003.783831]  cache: parent cpu1 should not be sleeping
Apr  3 20:48:59 FRDL kernel: [64003.784128] CPU1 is up
Apr  3 20:48:59 FRDL kernel: [64003.784166] smpboot: Booting Node 0 Processor 2 APIC 0x2
Apr  3 20:48:59 FRDL kernel: [64003.786678]  cache: parent cpu2 should not be sleeping
Apr  3 20:48:59 FRDL kernel: [64003.786989] CPU2 is up
Apr  3 20:48:59 FRDL kernel: [64003.787018] smpboot: Booting Node 0 Processor 3 APIC 0x3
Apr  3 20:48:59 FRDL kernel: [64003.789518]  cache: parent cpu3 should not be sleeping
Apr  3 20:48:59 FRDL kernel: [64003.789819] CPU3 is up
Apr  3 20:48:59 FRDL kernel: [64003.789846] smpboot: Booting Node 0 Processor 4 APIC 0x4
Apr  3 20:48:59 FRDL kernel: [64003.792349]  cache: parent cpu4 should not be sleeping
Apr  3 20:48:59 FRDL kernel: [64003.792674] CPU4 is up
Apr  3 20:48:59 FRDL kernel: [64003.792701] smpboot: Booting Node 0 Processor 5 APIC 0x5
Apr  3 20:48:59 FRDL kernel: [64003.795200]  cache: parent cpu5 should not be sleeping
Apr  3 20:48:59 FRDL kernel: [64003.795536] CPU5 is up
Apr  3 20:48:59 FRDL kernel: [64003.795561] smpboot: Booting Node 0 Processor 6 APIC 0x6
Apr  3 20:48:59 FRDL kernel: [64003.798073]  cache: parent cpu6 should not be sleeping
Apr  3 20:48:59 FRDL kernel: [64003.798449] CPU6 is up
Apr  3 20:48:59 FRDL kernel: [64003.798476] smpboot: Booting Node 0 Processor 7 APIC 0x7
Apr  3 20:48:59 FRDL kernel: [64003.801002]  cache: parent cpu7 should not be sleeping
Apr  3 20:48:59 FRDL kernel: [64003.801498] CPU7 is up
Apr  3 20:48:59 FRDL kernel: [64003.808403] ACPI: Waking up from system sleep state S3
Apr  3 20:48:59 FRDL kernel: [64004.502476] PM: noirq resume of devices complete after 40.233 msecs
Apr  3 20:48:59 FRDL kernel: [64004.502856] PM: early resume of devices complete after 0.361 msecs
Apr  3 20:48:59 FRDL kernel: [64004.502953] ACPI: EC: event unblocked
Apr  3 20:48:59 FRDL kernel: [64004.503566] sd 0:0:0:0: [sda] Starting disk
Apr  3 20:48:59 FRDL kernel: [64004.575449] xhci_hcd 0000:00:14.0: port 3 resume PLC timeout
Apr  3 20:48:59 FRDL kernel: [64004.652573] r8169 0000:0b:00.0 eno1: link down
Apr  3 20:48:59 FRDL kernel: [64004.814436] usb 3-4: reset full-speed USB device number 2 using xhci_hcd
Apr  3 20:48:59 FRDL kernel: [64004.826165] usb 1-1.3: reset high-speed USB device number 4 using ehci-pci
Apr  3 20:48:59 FRDL kernel: [64004.826188] usb 2-1.6: reset full-speed USB device number 3 using ehci-pci
Apr  3 20:48:59 FRDL kernel: [64004.829380] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  3 20:48:59 FRDL kernel: [64004.829402] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Apr  3 20:48:59 FRDL kernel: [64004.836856] ata5.00: configured for UDMA/100
Apr  3 20:48:59 FRDL kernel: [64004.913873] ata1.00: configured for UDMA/133
Apr  3 20:48:59 FRDL kernel: [64005.014204] usb 1-1.1: reset full-speed USB device number 3 using ehci-pci
Apr  3 20:48:59 FRDL kernel: [64005.502038] PM: resume of devices complete after 999.189 msecs
Apr  3 20:48:59 FRDL kernel: [64005.502207] usb 2-1.6:1.0: rebind failed: -517
Apr  3 20:48:59 FRDL kernel: [64005.502209] usb 2-1.6:1.1: rebind failed: -517
Apr  3 20:48:59 FRDL kernel: [64005.502598] PM: Finishing wakeup.
Apr  3 20:48:59 FRDL kernel: [64005.502599] OOM killer enabled.
Apr  3 20:48:59 FRDL systemd[1]: Time has been changed
Apr  3 20:48:59 FRDL acpid: client 1303[0:0] has disconnected
Apr  3 20:48:59 FRDL systemd[1916]: Time has been changed
Apr  3 20:48:59 FRDL systemd[1]: Starting Load/Save RF Kill Switch Status...
Apr  3 20:48:59 FRDL kernel: [64005.502600] Restarting tasks ... done.
Apr  3 20:48:59 FRDL systemd[1]: bluetooth.target: Unit not needed anymore. Stopping.
Apr  3 20:48:59 FRDL systemd[1]: Stopped target Bluetooth.
Apr  3 20:48:59 FRDL systemd[1]: Reached target Bluetooth.
Apr  3 20:48:59 FRDL systemd[1]: Started Load/Save RF Kill Switch Status.
Apr  3 20:49:00 FRDL systemd-sleep[23677]: System resumed.
Apr  3 20:49:00 FRDL systemd-sleep[23677]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Apr  3 20:49:00 FRDL kernel: [64005.996798] psmouse serio1: synaptics: queried max coordinates: x [..5684], y [..4862]
Apr  3 20:49:00 FRDL acpid: client connected from 1303[0:0]
Apr  3 20:49:00 FRDL acpid: 1 client rule loaded
Apr  3 20:49:00 FRDL kernel: [64006.051021] psmouse serio1: synaptics: queried min coordinates: x [1258..], y [992..]
Apr  3 20:49:02 FRDL systemd-sleep[23677]: /dev/sda:
Apr  3 20:49:02 FRDL systemd-sleep[23677]:  setting Advanced Power Management level to 0x80 (128)
Apr  3 20:49:02 FRDL systemd-sleep[23677]:  APM_level#011= 128
Apr  3 20:49:03 FRDL systemd-sleep[23677]: /dev/sda:
Apr  3 20:49:03 FRDL systemd-sleep[23677]:  setting standby to 36 (3 minutes)
Apr  3 20:49:03 FRDL systemd-sleep[23706]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Apr  3 20:49:03 FRDL systemd[1]: Started Suspend.
Apr  3 20:49:03 FRDL systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Apr  3 20:49:03 FRDL systemd[1]: Stopped target Sleep.
Apr  3 20:49:03 FRDL systemd[1]: Reached target Suspend.
Apr  3 20:49:03 FRDL systemd[1]: suspend.target: Unit is bound to inactive unit systemd-suspend.service. Stopping, too.
Apr  3 20:49:03 FRDL systemd[1]: Stopped target Suspend.
Apr  3 20:49:03 FRDL systemd[1]: Started Run anacron jobs at resume.
Apr  3 20:49:03 FRDL NetworkManager[1176]: <info>  [1522781343.1365] manager: wake requested (sleeping: yes  enabled: yes)
Apr  3 20:49:03 FRDL NetworkManager[1176]: <info>  [1522781343.1366] manager: waking up...
Apr  3 20:49:03 FRDL NetworkManager[1176]: <info>  [1522781343.1369] device (eno1): state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Apr  3 20:49:03 FRDL NetworkManager[1176]: <info>  [1522781343.1642] device (wlo1): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr  3 20:49:03 FRDL kernel: [64008.940583] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
Apr  3 20:49:03 FRDL kernel: [64008.953882] iwlwifi 0000:0a:00.0: Radio type=0x2-0x0-0x0
Apr  3 20:49:03 FRDL kernel: [64009.229301] iwlwifi 0000:0a:00.0: Radio type=0x2-0x0-0x0
Apr  3 20:49:03 FRDL kernel: [64009.289940] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
Apr  3 20:49:03 FRDL NetworkManager[1176]: <info>  [1522781343.5152] device (eno1): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr  3 20:49:03 FRDL kernel: [64009.291357] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
Apr  3 20:49:03 FRDL NetworkManager[1176]: <info>  [1522781343.6336] manager: NetworkManager state is now DISCONNECTED
Apr  3 20:49:03 FRDL kernel: [64009.408220] r8169 0000:0b:00.0 eno1: link down
Apr  3 20:49:03 FRDL kernel: [64009.408292] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
Apr  3 20:49:03 FRDL wpa_supplicant[1418]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Apr  3 20:49:03 FRDL wpa_supplicant[1418]: dbus: Failed to construct signal
Apr  3 20:49:03 FRDL NetworkManager[1176]: <info>  [1522781343.6861] device (wlo1): supplicant interface state: starting -> ready
Apr  3 20:49:03 FRDL NetworkManager[1176]: <info>  [1522781343.6862] device (wlo1): state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr  3 20:49:03 FRDL kernel: [64009.462409] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
```

---

### Post by HermanAB on 2018-04-04
Usually, when the battery gets critically low, the laptop will wake up from suspend and then either hibernate or shut down.  Check your power management settings.

The HDD will not get damaged.  Laptop HDDs have an acceleration sensor and will lift the heads when there is too much vibration.

---

