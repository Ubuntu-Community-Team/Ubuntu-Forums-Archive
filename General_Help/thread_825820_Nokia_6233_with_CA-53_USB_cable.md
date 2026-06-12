---
title: "Nokia 6233 with CA-53 USB cable"
date: 2008-06-11
forum: General Help
---

### Post by Kemono on 2008-06-11
Hi guys,

my brother has a Nokia 6233 I want to connect to my computer with a CA-53 USB cable. I choose the storage option from the phone and it mounts fine. The problem is, I can't open the files. They are there but won't open. When I try to copy them the copy dialog box just stays at 0. Is there a way to make it work properly?

---

### Post by Kemono on 2008-06-12
Bump.

---

### Post by loell on 2008-06-12
have you tried to mount or open it with root?

---

### Post by Kemono on 2008-06-12
I thought the privileges of removable drives are always assigned to root(like how the partitions are). Anyway, I'll check it out when he gets home. Anything else I should try/know about?

---

### Post by fr33styl3r on 2008-07-17
So, did it work? I have exactly the same problem..:(
Tried to copy the file from the phone with Midnight Commander run as root - no changes.
/var/log/messages says something like "USB device reset" (can provide the full log if needed...)

---

### Post by dreamer84 on 2009-02-14
has anyone found a solution yet? I still have this problem. Nautilus shows all the files on the phones card, but as soon as I try to access them, everything concerning USB screws up - I even have to restart in order to mount a simple USB-stick which otherwise works fine :-/ and I hate having to boot to windows just because of to pics i've taken - nope, don't have bluetooth. maybe IrDA?

edit: just tested it again, here some log:
```

sudo tail -fn0 /var/log/messages
Feb 14 12:20:29 tobias-laptop kernel: [ 1006.745108] usb 2-1: new full speed USB device using uhci_hcd and address 2
Feb 14 12:20:29 tobias-laptop kernel: [ 1006.918270] usb 2-1: configuration #1 chosen from 1 choice
Feb 14 12:20:29 tobias-laptop kernel: [  365.911842] usbcore: registered new interface driver libusual
Feb 14 12:20:29 tobias-laptop kernel: [  755.384001] Initializing USB Mass Storage driver...
Feb 14 12:20:29 tobias-laptop kernel: [  755.407267] scsi2 : SCSI emulation for USB Mass Storage devices
Feb 14 12:20:29 tobias-laptop kernel: [  755.421876] usbcore: registered new interface driver usb-storage
Feb 14 12:20:29 tobias-laptop kernel: [  755.421893] USB Mass Storage support registered.
Feb 14 12:20:34 tobias-laptop kernel: [ 1013.838300] scsi 2:0:0:0: Direct-Access     Nokia    Nokia 6233       0000 PQ: 0 ANSI: 4
Feb 14 12:20:34 tobias-laptop kernel: [ 1013.854262] sd 2:0:0:0: [sdb] 3987457 512-byte hardware sectors (2042 MB)
Feb 14 12:20:34 tobias-laptop kernel: [ 1013.861246] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 14 12:20:34 tobias-laptop kernel: [ 1013.870242] sd 2:0:0:0: [sdb] 3987457 512-byte hardware sectors (2042 MB)
Feb 14 12:20:34 tobias-laptop kernel: [ 1013.877279] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 14 12:20:35 tobias-laptop kernel: [ 1013.877309]  sdb: sdb1
Feb 14 12:20:35 tobias-laptop kernel: [  368.431689] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Feb 14 12:20:35 tobias-laptop kernel: [  368.431749] sd 2:0:0:0: Attached scsi generic sg2 type 0
Feb 14 12:20:35 tobias-laptop kernel: [  368.554426] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
Feb 14 12:20:35 tobias-laptop kernel: [  368.554440] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
Feb 14 12:21:56 tobias-laptop kernel: [ 1105.909862] usb 2-1: reset full speed USB device using uhci_hcd and address 2
Feb 14 12:22:26 tobias-laptop kernel: [  413.956923] usb 2-1: reset full speed USB device using uhci_hcd and address 2
Feb 14 12:22:57 tobias-laptop kernel: [ 1176.846723] usb 2-1: reset full speed USB device using uhci_hcd and address 2
Feb 14 12:23:07 tobias-laptop kernel: [ 1190.772153] usb 2-1: reset full speed USB device using uhci_hcd and address 2
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.702085] usb 2-1: USB disconnect, address 2
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.702725] sd 2:0:0:0: Device offlined - not ready after error recovery
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.703550] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.703562] end_request: I/O error, dev sdb, sector 618176
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.703618] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.703627] end_request: I/O error, dev sdb, sector 618416
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.703657] lost page write due to I/O error on sdb1
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.705531] sd 2:0:0:0: [sdb] READ CAPACITY failed
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.705538] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.705547] sd 2:0:0:0: [sdb] Sense not available.
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.705576] sd 2:0:0:0: [sdb] Write Protect is off
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.718297] sd 2:0:0:0: [sdb] READ CAPACITY failed
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.718310] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.718320] sd 2:0:0:0: [sdb] Sense not available.
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.720213] sd 2:0:0:0: [sdb] Write Protect is off
Feb 14 12:23:18 tobias-laptop kernel: [ 1203.833769] usb 2-1: new full speed USB device using uhci_hcd and address 3

```

as soon as I try to access files things go wrong. even cp on gnome-terminal froze! lsusb also froze until I removed the cable again. nasty. any help is apreciated

---

### Post by AlexandreS on 2009-05-17
I can't really help you, but I can report that on my kubuntu jaunty it works out of the box. I can open the files, copy or delete them. I also used the cable to install jars.

---

