---
title: "Photosmart c4280 connection issues"
date: 2008-01-30
forum: General Help
---

### Post by onthefritz on 2008-01-30
My new HP Photosmart C4280 printer is playing tricks on me.

For some reason my printer doesn't want to stay connected to my system. Even in HPLIP if I refresh it keeps dropping and re adding the printer.  I have tried different USB ports and cables. 

Here is the output of dmesg command

```
[ 4126.227445] scsi 53:0:0:0: rejecting I/O to dead device
[ 4126.227449] scsi 53:0:0:0: rejecting I/O to dead device
[ 4126.227452] scsi 53:0:0:0: [sdb] READ CAPACITY failed
[ 4126.227454] scsi 53:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4126.227457] scsi 53:0:0:0: [sdb] Sense not available.
[ 4126.227460] scsi 53:0:0:0: rejecting I/O to dead device
[ 4126.227464] scsi 53:0:0:0: [sdb] Write Protect is off
[ 4126.227466] scsi 53:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 4126.227467] scsi 53:0:0:0: [sdb] Assuming drive cache: write through
[ 4126.227488] scsi 53:0:0:0: rejecting I/O to dead device
[ 4126.335671] usb 3-1: new high speed USB device using ehci_hcd and address 54
[ 4126.447575] usb 3-1: device descriptor read/64, error -71
[ 4126.663388] usb 3-1: device descriptor read/64, error -71
[ 4126.879218] usb 3-1: new high speed USB device using ehci_hcd and address 55
[ 4126.991113] usb 3-1: device descriptor read/64, error -71
[ 4127.206925] usb 3-1: device descriptor read/64, error -71
[ 4127.422738] usb 3-1: new high speed USB device using ehci_hcd and address 56
[ 4127.830379] usb 3-1: device not accepting address 56, error -71
[ 4127.942292] usb 3-1: new high speed USB device using ehci_hcd and address 57
[ 4128.349954] usb 3-1: device not accepting address 57, error -71

```

I'm not sure what else to do....

I'm running Ubuntu 7.10

OTF

---

### Post by onthefritz on 2008-01-31
Here is a little extra info:

Output of /var/log/daemon.log
```

Jan 30 20:02:21 OnTheDesk NetworkManager: <debug> [1201748541.116163] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_if3_scsi_host_scsi_device_lun0_scsi_generic').
Jan 30 20:02:21 OnTheDesk NetworkManager: <debug> [1201748541.127179] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_HP_Photosmart_C4280_CN7BMRC24204VP_0_0').
Jan 30 20:02:21 OnTheDesk NetworkManager: <debug> [1201748541.132591] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_if3_scsi_host_scsi_device_lun0').
Jan 30 20:02:21 OnTheDesk NetworkManager: <debug> [1201748541.135116] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_if3_scsi_host').
Jan 30 20:02:21 OnTheDesk NetworkManager: <debug> [1201748541.142703] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_usbraw').
Jan 30 20:02:21 OnTheDesk NetworkManager: <debug> [1201748541.148516] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_if3').
Jan 30 20:02:21 OnTheDesk NetworkManager: <debug> [1201748541.152819] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP').

```

Output of /var/log/debug
```

Jan 30 19:45:11 OnTheDesk hal_lpadmin: URIs: ['hp:/usb/Photosmart_C4200_series?serial=CN7BMRC24204VP', 'usb://HP/Photosmart%20C4200%20series?serial=CN7BMRC24204VP', 'hal:///org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_printer_CN7BMRC24204VP']
Jan 30 19:45:13 OnTheDesk NetworkManager: <debug> [1201747513.885406] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_printer_CN7BMRC24204VP').
Jan 30 19:45:14 OnTheDesk kernel: [ 3100.947839] usb-storage: device scan complete
Jan 30 19:45:15 OnTheDesk NetworkManager: <debug> [1201747515.301674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_if3_scsi_host').
Jan 30 19:45:15 OnTheDesk NetworkManager: <debug> [1201747515.302246] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_if3_scsi_host_scsi_device_lun0').
Jan 30 19:45:15 OnTheDesk NetworkManager: <debug> [1201747515.329539] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_if3_scsi_host_scsi_device_lun0_scsi_generic').
Jan 30 19:45:19 OnTheDesk NetworkManager: <debug> [1201747519.666519] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_if0').
Jan 30 19:45:20 OnTheDesk kernel: [ 3106.464818] usb-storage: device found at 96
Jan 30 19:45:20 OnTheDesk kernel: [ 3106.464820] usb-storage: waiting for device to settle before scanning
Jan 30 19:45:20 OnTheDesk NetworkManager: <debug> [1201747520.569937] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_printer_CN7BMRC24204VP').
Jan 30 19:45:20 OnTheDesk NetworkManager: <debug> [1201747520.571073] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Jan 30 19:45:20 OnTheDesk NetworkManager: <debug> [1201747520.572849] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7BMRC24204VP_if2').
Jan 30 19:45:20 OnTheDesk NetworkManager: <debug> [1201747520.576332] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop

```

Output of /var/log/user.log
```

Jan 30 20:00:12 OnTheDesk python: hp-probe[14359]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Jan 30 20:00:12 OnTheDesk python: hp-probe[14359]: warning: check to make sure your devices are properly connected and powered on.
Jan 30 20:01:32 OnTheDesk python: hp-setup[14419]: error: No devices found.Please make sure your printer is properly connected and powered-on.
Jan 30 20:01:35 OnTheDesk python: hp-probe[14471]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Jan 30 20:01:35 OnTheDesk python: hp-probe[14471]: warning: check to make sure your devices are properly connected and powered on.
Jan 30 20:01:36 OnTheDesk python: hp-probe[14473]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Jan 30 20:01:36 OnTheDesk python: hp-probe[14473]: warning: check to make sure your devices are properly connected and powered on.
Jan 30 20:02:10 OnTheDesk python: io/hpmud/musb.c 1003: unable to open hp:/usb/Photosmart_C4200_series?serial=CN7BMRC24204VP
Jan 30 20:02:10 OnTheDesk python: hp-setup[14419]: error: Unable to communicate with device (code=12): hp:/usb/Photosmart_C4200_series?serial=CN7BMRC24204VP
Jan 30 20:02:10 OnTheDesk python: hp-setup[14419]: error: Unable to print to printer.Please check device and try again.

```

Output of /var/log/cups/error_log
```

I [31/Jan/2008:07:35:09 -0700] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 36 types, 40 filters...
D [31/Jan/2008:07:35:09 -0700] Loading printer HP_Photosmart...
D [31/Jan/2008:07:35:09 -0700] Loading printer Photosmart_C4200...
D [31/Jan/2008:07:35:09 -0700] Loading class Printer...
I [31/Jan/2008:07:35:09 -0700] Loading job cache file "/var/cache/cups/job.cache"...
D [31/Jan/2008:07:35:09 -0700] [Job 17] Loading from cache...
I [31/Jan/2008:07:35:09 -0700] Full reload complete.
I [31/Jan/2008:07:35:09 -0700] Listening to 127.0.0.1:631 on fd 2...
I [31/Jan/2008:07:35:09 -0700] Listening to /var/run/cups/cups.sock on fd 4...
I [31/Jan/2008:07:35:09 -0700] Resuming new connection processing...

```

Hope someone can help out...

OTF

---

### Post by onthefritz on 2008-01-31
As it turns out, my Ubuntu 7.10 laptop can access it fine. I will have to compare the settings and figure out what could be causing the issue. 

OTF

---

