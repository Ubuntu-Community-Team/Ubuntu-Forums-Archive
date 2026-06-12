---
title: "USB Flash Drive Issues"
date: 2007-10-13
forum: General Help
---

### Post by Zipster90 on 2007-10-13
I've just installed Feisty on my Dell E1505, and I can't seem to get my Lexar USB flash drive to be detected. No matter what port I plug it into, it just won't work. I've used USB drives in the past in Linux with no complaint, and I'm pretty sure this drive still works. Any pointers?:confused:

---

### Post by geirha on 2007-10-13
open a terminal and type ```
tail -f /var/log/syslog
```. Then insert the usb drive. The terminal should now get some new lines saying it detects it and mounts it, or in your case  it should hopefully give some error message that describes why it doesn't work.

---

### Post by Zipster90 on 2007-10-13
Thanks for the tip. It detected and mounted the drive, but it doesn't show up on the desktop or anywhere that I can access it. Is there another step?

---

### Post by chejrw on 2007-10-30
Bumping to the top for furthur response - I am having the same problem.

Output of tail is:

```
Oct 30 16:21:44 UMCP-Justin kernel: [100970.948468] usb 5-4.1: new high speed USB device using ehci_hcd and address 4
Oct 30 16:21:44 UMCP-Justin kernel: [100971.053994] usb 5-4.1: configuration #1 chosen from 1 choice
Oct 30 16:21:44 UMCP-Justin kernel: [100971.054748] scsi3 : SCSI emulation for USB Mass Storage devices
Oct 30 16:21:44 UMCP-Justin kernel: [100971.054821] usb-storage: device found at 4
Oct 30 16:21:44 UMCP-Justin kernel: [100971.054825] usb-storage: waiting for device to settle before scanning
Oct 30 16:21:44 UMCP-Justin NetworkManager: <debug> [1193775704.475125] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_8ec_8_0EC1B65060E38951'). 
Oct 30 16:21:44 UMCP-Justin NetworkManager: <debug> [1193775704.583117] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_8ec_8_0EC1B65060E38951_if0'). 
Oct 30 16:21:44 UMCP-Justin NetworkManager: <debug> [1193775704.662943] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_8ec_8_0EC1B65060E38951_usbraw'). 
Oct 30 16:21:49 UMCP-Justin kernel: [100976.052328] usb-storage: device scan complete
Oct 30 16:21:49 UMCP-Justin kernel: [100976.052987] scsi 3:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.04 PQ: 0 ANSI: 0 CCS
Oct 30 16:21:49 UMCP-Justin kernel: [100976.335840] sd 3:0:0:0: [sdb] 1003520 512-byte hardware sectors (514 MB)
Oct 30 16:21:49 UMCP-Justin kernel: [100976.336461] sd 3:0:0:0: [sdb] Write Protect is off
Oct 30 16:21:49 UMCP-Justin kernel: [100976.336467] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
Oct 30 16:21:49 UMCP-Justin kernel: [100976.336471] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Oct 30 16:21:49 UMCP-Justin kernel: [100976.338958] sd 3:0:0:0: [sdb] 1003520 512-byte hardware sectors (514 MB)
Oct 30 16:21:49 UMCP-Justin kernel: [100976.339583] sd 3:0:0:0: [sdb] Write Protect is off
Oct 30 16:21:49 UMCP-Justin kernel: [100976.339589] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
Oct 30 16:21:49 UMCP-Justin kernel: [100976.339593] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Oct 30 16:21:49 UMCP-Justin kernel: [100976.339599]  sdb: sdb1
Oct 30 16:21:49 UMCP-Justin kernel: [100976.340585] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Oct 30 16:21:49 UMCP-Justin kernel: [100976.340668] sd 3:0:0:0: Attached scsi generic sg3 type 0
Oct 30 16:21:49 UMCP-Justin NetworkManager: <debug> [1193775709.907114] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_8ec_8_0EC1B65060E38951_if0_scsi_host'). 
Oct 30 16:21:50 UMCP-Justin NetworkManager: <debug> [1193775710.202016] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_8ec_8_0EC1B65060E38951_if0_scsi_host_scsi_device_lun0'). 
Oct 30 16:21:50 UMCP-Justin NetworkManager: <debug> [1193775710.219085] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_8ec_8_0EC1B65060E38951_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 30 16:21:50 UMCP-Justin NetworkManager: <debug> [1193775710.363146] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTraveler_2_0_0EC1B65060E38951_0_0'). 
Oct 30 16:21:50 UMCP-Justin NetworkManager: <debug> [1193775710.415536] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_B423_1C77'). 

```

It claims 'new decive added' - and yet it does not appear on the desktop, in 'computer' or anywhere else that I can find.  Any help appreciated.

---

