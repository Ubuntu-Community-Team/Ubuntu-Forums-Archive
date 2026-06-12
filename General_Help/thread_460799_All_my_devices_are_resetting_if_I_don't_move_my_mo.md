---
title: "All my devices are resetting if I don't move my mouse for a few minutes"
date: 2007-06-01
forum: General Help
---

### Post by crazyflax on 2007-06-01
If I turn on the computer, everything's fine. If I leave the computer on and don't move the mouse for about ten minutes my ubuntu feisty fawn 7.04 suspends all my devices. I started tail on syslog and then where it says MARK is where I stopped using the mouse. This is what it gave me when I tail syslog:

mike@mike-desktop:~$ sudo tail -f /var/log/syslog
Password:
Jun  1 01:17:16 mike-desktop gconfd (mike-5295): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  1 01:17:16 mike-desktop gconfd (mike-5295): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  1 01:17:21 mike-desktop kernel: [   73.055626] NTFS driver 2.1.28 [Flags: R/O MODULE].
Jun  1 01:17:21 mike-desktop kernel: [   73.059480] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
Jun  1 01:17:21 mike-desktop hald: mounted /dev/sda1 on behalf of uid 1000
Jun  1 01:17:21 mike-desktop kernel: [   73.499917] NTFS volume version 3.1.
Jun  1 01:17:24 mike-desktop gconfd (mike-5295): Resolved address "xml:readwrite:/home/mike/.gconf" to a writable configuration source at position 0
Jun  1 01:17:25 mike-desktop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jun  1 01:17:25 mike-desktop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun  1 01:36:58 mike-desktop -- MARK --
Jun  1 01:45:56 mike-desktop apmd[4681]: Suspending now
Jun  1 01:45:56 mike-desktop kernel: [ 1786.725448] platform bluetooth: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.725466] sd 0:0:0:0: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.725476] ac97 0-0:STAC9708,11: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.725488] platform iTCO_wdt: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.725493] usb-storage 2-2:1.0: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.725497] usb 2-2: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738883]  usbdev2.2_ep86: PM: suspend 0->2, parent 2-1:1.2 already 2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738892]  usbdev2.2_ep85: PM: suspend 0->2, parent 2-1:1.2 already 2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738897]  usbdev2.2_ep05: PM: suspend 0->2, parent 2-1:1.2 already 2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738901] usb 2-1:1.2: PM: suspend 2-->2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738906] usblp 2-1:1.1: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738910]  usbdev2.2_ep82: PM: suspend 0->2, parent 2-1:1.0 already 2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738915]  usbdev2.2_ep81: PM: suspend 0->2, parent 2-1:1.0 already 2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738919]  usbdev2.2_ep01: PM: suspend 0->2, parent 2-1:1.0 already 2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738923] usb 2-1:1.0: PM: suspend 2-->2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.738927] usb 2-1: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.754959] hub 2-0:1.0: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.754966] usb usb2: suspend, may wakeup
Jun  1 01:45:56 mike-desktop kernel: [ 1786.754990]  usbdev1.1_ep81: PM: suspend 0->2, parent 1-0:1.0 already 2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.754994] hub 1-0:1.0: PM: suspend 2-->2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.754998] hub 1-0:1.0: PM: suspend 2->2, parent usb1 already 2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.755002]  usbdev1.1_ep00: PM: suspend 0->2, parent usb1 already 2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.755006] usb usb1: PM: suspend 2-->2
Jun  1 01:45:56 mike-desktop kernel: [ 1786.755011] ide-cdrom 1.1: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.755033] ide-cdrom 1.0: suspend
Jun  1 01:45:56 mike-desktop kernel: [ 1786.755046] ide-disk 0.0: suspend
Jun  1 01:45:57 mike-desktop kernel: [ 1787.106440] platform floppy.0: suspend
Jun  1 01:45:57 mike-desktop kernel: [ 1787.106584] platform vesafb.0: suspend
Jun  1 01:45:57 mike-desktop kernel: [ 1787.106703] platform eisa.0: suspend
Jun  1 01:45:57 mike-desktop kernel: [ 1787.106815] i8042 i8042: suspend
Jun  1 01:45:57 mike-desktop kernel: [ 1787.825898] sda : READ CAPACITY failed.
Jun  1 01:45:57 mike-desktop kernel: [ 1787.825901] sda : status=0, message=00, host=7, driver=00 
Jun  1 01:45:57 mike-desktop kernel: [ 1787.825908] sda : sense not available. 
Jun  1 01:45:57 mike-desktop kernel: [ 1787.826946] sda: Write Protect is off
Jun  1 01:45:57 mike-desktop kernel: [ 1787.826952] sda: Mode Sense: 00 00 00 00
Jun  1 01:45:57 mike-desktop kernel: [ 1787.826956] sda: assuming drive cache: write through
Jun  1 01:45:58 mike-desktop kernel: [ 1788.009324] serial8250 serial8250: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.010169] pcspkr pcspkr: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.010307] ENS1371 0000:02:0a.0: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.025349] 8139too 0000:02:03.0: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.041334] pci 0000:01:00.0: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.041537] uhci_hcd 0000:00:1f.4: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.041707] pci 0000:00:1f.3: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.041854] uhci_hcd 0000:00:1f.2: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.042020] PIIX_IDE 0000:00:1f.1: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.042180] pci 0000:00:1f.0: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.042329] pci 0000:00:1e.0: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.042475] pci 0000:00:01.0: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.042611] agpgart-intel 0000:00:00.0: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.042792] serial 00:10: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.043007] pnp: Device 00:10 disabled.
Jun  1 01:45:58 mike-desktop kernel: [ 1788.043126] parport_pc 00:0f: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.043374] pnp: Device 00:0f disabled.
Jun  1 01:45:58 mike-desktop kernel: [ 1788.043492] pnp 00:0d: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.043589] serial 00:0c: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.043795] pnp: Device 00:0c disabled.
Jun  1 01:45:58 mike-desktop kernel: [ 1788.043914] i8042 aux 00:0b: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.044089] pnp: Device 00:0b disabled.
Jun  1 01:45:58 mike-desktop kernel: [ 1788.044208] pnp 00:0a: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.044305] system 00:09: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.044409] system 00:08: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.044513] pnp 00:07: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.044610] pnp 00:06: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.044707] pnp 00:05: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.044804] i8042 kbd 00:04: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.044915] pnp 00:03: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045017] pnp 00:02: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045114] pnp 00:01: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045210] pnp 00:00: suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045311] platform bluetooth: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045326] platform iTCO_wdt: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045335] platform floppy.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045338] platform vesafb.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045342] platform eisa.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045346] i8042 i8042: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045351] serial8250 serial8250: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045481] pcspkr pcspkr: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045487] ENS1371 0000:02:0a.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045491] 8139too 0000:02:03.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045494] pci 0000:01:00.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045497] pci 0000:00:1f.3: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045501] PIIX_IDE 0000:00:1f.1: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045504] pci 0000:00:1f.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045507] pci 0000:00:1e.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045510] pci 0000:00:01.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.045513] agpgart-intel 0000:00:00.0: LATE suspend
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671543] agpgart-intel 0000:00:00.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671553] pci 0000:00:01.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671556] pci 0000:00:1e.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671560] pci 0000:00:1f.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671564] PIIX_IDE 0000:00:1f.1: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671569] uhci_hcd 0000:00:1f.2: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671572] pci 0000:00:1f.3: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671576] uhci_hcd 0000:00:1f.4: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671579] pci 0000:01:00.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671583] 8139too 0000:02:03.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671587] ENS1371 0000:02:0a.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671592] pcspkr pcspkr: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671691] serial8250 serial8250: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671696] i8042 i8042: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671699] platform eisa.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671703] platform vesafb.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671706] platform floppy.0: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671715] platform iTCO_wdt: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.671726] platform bluetooth: EARLY resume
Jun  1 01:45:58 mike-desktop kernel: [ 1788.764371] pnp 00:00: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.764489] pnp 00:01: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.764588] pnp 00:02: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.764688] pnp 00:03: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.764787] i8042 kbd 00:04: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.764792] pnp: Device 00:04 does not support activation.
Jun  1 01:45:58 mike-desktop kernel: [ 1788.765060] pnp 00:05: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.765159] pnp 00:06: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.765258] pnp 00:07: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.765358] system 00:08: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.765464] system 00:09: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.765570] pnp 00:0a: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.765669] i8042 aux 00:0b: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.765842] pnp: Device 00:0b activated.
Jun  1 01:45:58 mike-desktop kernel: [ 1788.765962] serial 00:0c: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.766172] pnp: Device 00:0c activated.
Jun  1 01:45:58 mike-desktop kernel: [ 1788.766295] pnp 00:0d: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.766395] parport_pc 00:0f: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.766646] pnp: Device 00:0f activated.
Jun  1 01:45:58 mike-desktop kernel: [ 1788.766767] serial 00:10: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.766976] pnp: Device 00:10 activated.
Jun  1 01:45:58 mike-desktop kernel: [ 1788.767098] agpgart-intel 0000:00:00.0: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.767296] pci 0000:00:01.0: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.767626] pci 0000:00:1e.0: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.767672] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Jun  1 01:45:58 mike-desktop kernel: [ 1788.767969] pci 0000:00:1f.0: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.768117] PIIX_IDE 0000:00:1f.1: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.768282] uhci_hcd 0000:00:1f.2: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.768299] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jun  1 01:45:58 mike-desktop kernel: [ 1788.768355] usb usb1: root hub lost power or was reset
Jun  1 01:45:58 mike-desktop kernel: [ 1788.768819] pci 0000:00:1f.3: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.768966] uhci_hcd 0000:00:1f.4: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.768982] PCI: Setting latency timer of device 0000:00:1f.4 to 64
Jun  1 01:45:58 mike-desktop kernel: [ 1788.769035] usb usb2: root hub lost power or was reset
Jun  1 01:45:58 mike-desktop kernel: [ 1788.769520] pci 0000:01:00.0: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.769682] 8139too 0000:02:03.0: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.788995] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jun  1 01:45:58 mike-desktop kernel: [ 1788.789213] ENS1371 0000:02:0a.0: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.807397] usb 2-1: USB disconnect, address 2
Jun  1 01:45:58 mike-desktop kernel: [ 1788.807841] drivers/usb/class/usblp.c: usblp0: removed
Jun  1 01:45:58 mike-desktop NetworkManager: <debug info>^I[1180676758.524008] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453_if0'). 
Jun  1 01:45:58 mike-desktop NetworkManager: <debug info>^I[1180676758.643951] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453_if1_printer_CN6ANEH43M0453'). 
Jun  1 01:45:58 mike-desktop NetworkManager: <debug info>^I[1180676758.647722] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453_if1'). 
Jun  1 01:45:58 mike-desktop kernel: [ 1788.965050] pcspkr pcspkr: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.965374] serial8250 serial8250: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.965514] i8042 i8042: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1788.966150] atkbd serio0: resuming
Jun  1 01:45:58 mike-desktop NetworkManager: <debug info>^I[1180676758.672713] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453_if2'). 
Jun  1 01:45:58 mike-desktop NetworkManager: <debug info>^I[1180676758.682632] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453_usbraw'). 
Jun  1 01:45:58 mike-desktop NetworkManager: <debug info>^I[1180676758.690458] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453'). 
Jun  1 01:45:58 mike-desktop kernel: [ 1789.008850] platform eisa.0: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1789.008992] psmouse serio1: resuming
Jun  1 01:45:58 mike-desktop kernel: [ 1789.079090] usb 2-1: new full speed USB device using uhci_hcd and address 4
Jun  1 01:45:58 mike-desktop kernel: [ 1789.273935] usb 2-1: configuration #1 chosen from 1 choice
Jun  1 01:45:59 mike-desktop kernel: [ 1789.280880] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4B11
Jun  1 01:45:59 mike-desktop kernel: [ 1789.281227] usb 2-2: USB disconnect, address 3
Jun  1 01:45:59 mike-desktop NetworkManager: <debug info>^I[1180676759.087279] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453'). 
Jun  1 01:45:59 mike-desktop NetworkManager: <debug info>^I[1180676759.210733] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453_if0'). 
Jun  1 01:45:59 mike-desktop kernel: [ 1789.522624] usb 2-2: new full speed USB device using uhci_hcd and address 5
Jun  1 01:45:59 mike-desktop kernel: [ 1789.697427] usb 2-2: configuration #1 chosen from 1 choice
Jun  1 01:45:59 mike-desktop kernel: [ 1789.700445] scsi1 : SCSI emulation for USB Mass Storage devices
Jun  1 01:45:59 mike-desktop kernel: [ 1789.700652] usb-storage: device found at 5
Jun  1 01:45:59 mike-desktop kernel: [ 1789.700655] usb-storage: waiting for device to settle before scanning
Jun  1 01:45:59 mike-desktop NetworkManager: <debug info>^I[1180676759.493162] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453_if2'). 
Jun  1 01:45:59 mike-desktop NetworkManager: <debug info>^I[1180676759.509638] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_if0_scsi_device_lun0_scsi_generic'). 
Jun  1 01:45:59 mike-desktop NetworkManager: <debug info>^I[1180676759.595968] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jun  1 01:45:59 mike-desktop hald[4371]: forcibly attempting to lazy unmount /dev/sda1 as enclosing drive was disconnected
Jun  1 01:45:59 mike-desktop kernel: [ 1790.052442] platform vesafb.0: resuming
Jun  1 01:45:59 mike-desktop kernel: [ 1790.052586] platform floppy.0: resuming
Jun  1 01:45:59 mike-desktop kernel: [ 1790.052706] ide-disk 0.0: resuming
Jun  1 01:46:02 mike-desktop kernel: [ 1792.774008] ide-cdrom 1.0: resuming
Jun  1 01:46:02 mike-desktop kernel: [ 1792.776805] ide-cdrom 1.1: resuming
Jun  1 01:46:02 mike-desktop kernel: [ 1792.779980] usb usb1: resuming
Jun  1 01:46:02 mike-desktop kernel: [ 1792.820360] usb usb2: resuming
Jun  1 01:46:02 mike-desktop kernel: [ 1792.820485] hub 2-0:1.0: resuming
Jun  1 01:46:02 mike-desktop kernel: [ 1792.820590] platform iTCO_wdt: resuming
Jun  1 01:46:02 mike-desktop kernel: [ 1792.820716] ac97 0-0:STAC9708,11: resuming
Jun  1 01:46:02 mike-desktop kernel: [ 1792.820850] platform bluetooth: resuming
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.600111] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_7E4A2F394A2EED99'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.713502] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_printer_CN6ANEH43M0453'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.921378] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_if0_scsi_device_lun0'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.921531] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_if0_scsi_host'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.921606] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_usbraw'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.921679] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_if0'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.921749] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.921820] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.925988] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_if0'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.930062] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_if0_scsi_host'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.934083] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_usbraw'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.937865] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4b11_CN6ANEH43M0453_usbraw'). 
Jun  1 01:46:02 mike-desktop NetworkManager: <debug info>^I[1180676762.970886] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTraveler_2_0_5B721C9715AF_0_0'). 
Jun  1 01:46:04 mike-desktop anacron[6444]: Anacron 2.3 started on 2007-06-01
Jun  1 01:46:04 mike-desktop anacron[6444]: Normal exit (0 jobs run)
Jun  1 01:46:05 mike-desktop kernel: [ 1794.698951] usb-storage: device scan complete
Jun  1 01:46:05 mike-desktop kernel: [ 1794.701954] scsi 1:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
Jun  1 01:46:05 mike-desktop kernel: [ 1794.707903] SCSI device sda: 7966720 512-byte hdwr sectors (4079 MB)
Jun  1 01:46:05 mike-desktop kernel: [ 1794.710927] sda: Write Protect is off
Jun  1 01:46:05 mike-desktop kernel: [ 1794.710936] sda: Mode Sense: 23 00 00 00
Jun  1 01:46:05 mike-desktop kernel: [ 1794.710940] sda: assuming drive cache: write through
Jun  1 01:46:05 mike-desktop kernel: [ 1794.722894] SCSI device sda: 7966720 512-byte hdwr sectors (4079 MB)
Jun  1 01:46:05 mike-desktop kernel: [ 1794.725882] sda: Write Protect is off
Jun  1 01:46:05 mike-desktop kernel: [ 1794.725889] sda: Mode Sense: 23 00 00 00
Jun  1 01:46:05 mike-desktop kernel: [ 1794.725893] sda: assuming drive cache: write through
Jun  1 01:46:05 mike-desktop kernel: [ 1794.725900]  sda: sda1
Jun  1 01:46:05 mike-desktop kernel: [ 1794.735021] sd 1:0:0:0: Attached scsi removable disk sda
Jun  1 01:46:05 mike-desktop kernel: [ 1794.735089] sd 1:0:0:0: Attached scsi generic sg0 type 0
Jun  1 01:46:05 mike-desktop NetworkManager: <debug info>^I[1180676765.439631] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_if0_scsi_host_scsi_device_lun0'). 
Jun  1 01:46:05 mike-desktop NetworkManager: <debug info>^I[1180676765.560719] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_5B721C9715AF_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jun  1 01:46:05 mike-desktop NetworkManager: <debug info>^I[1180676765.570375] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTraveler_2_0_5B721C9715AF_0_0'). 
Jun  1 01:46:05 mike-desktop NetworkManager: <debug info>^I[1180676765.937817] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_7E4A2F394A2EED99'). 
Jun  1 01:46:06 mike-desktop kernel: [ 1795.450990] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
Jun  1 01:46:06 mike-desktop hald: mounted /dev/sda1 on behalf of uid 1000
Jun  1 01:46:06 mike-desktop kernel: [ 1795.900422] NTFS volume version 3.1.

No idea what to do and I'm new to Linux so any help is very appreciated!

---

### Post by crazyflax on 2007-06-01
bumpity bump

---

### Post by crazyflax on 2007-06-04
Any help will be greatly appreciated!

---

### Post by crazyflax on 2007-06-04
Bumpity bump

---

### Post by pjman on 2007-06-04
I'm getting the same error trying to boot my Feisty LiveCD

```

NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
```

If I find anything I'll let you know.

---

### Post by crazyflax on 2007-06-05
Thanks pjman. Also, when my devices reset I lose internet connectivity even though it still detects my wired connection.

---

### Post by crazyflax on 2007-06-07
Yea I'm a noob at Linux so I don't really know what I should be doing to test this. Anyone have any ideas?

---

### Post by rivode on 2007-06-15
I don't really know, but this line seems a bit odd to me:

```

Jun 1 01:45:56 mike-desktop apmd[4681]: Suspending now
```

I think apmd is what looks after the computer's power (in older computers, anyway).  It's as if it's trying to suspend your whole computer!  You can see it first suspending Bluetooth, then AC97 (your sound), then USB, and so on.  Then it starts everything back up!

Perhaps check System/Preferences/Power Mangement, and see if there's anything strange there.

---

### Post by crazyflax on 2007-06-19
I would've replied sooner but I haven't had access to a computer the last couple days. I went to my preferences before and changed it to never sleep after a specific time  for both the computer and display.

---

### Post by crazyflax on 2007-06-20
Now I can still use the internet after it suspends all the devices but I don't get any sound. Here is my xorg.config:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by crazyflax on 2007-06-23
Anybody?

---

### Post by crazyflax on 2007-07-23
I just uninstalled the apmd packages and it's fine now.

---

