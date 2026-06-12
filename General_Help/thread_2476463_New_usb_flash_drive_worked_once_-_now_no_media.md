---
title: "New usb flash drive worked once - now no media"
date: 2022-06-27
forum: General Help
---

### Post by MimziM on 2022-06-27
I got a new 128GB metal Samsung flash drive, I backed up some data, first time using it, and the next day its not working?!? This was done on a new HP (only has usb-c, so used an OTG) running windows 11. I have tried on different windows machines (7, 10, 11) different ports (usb 2.0, usb 3.0, usb C) and many variants (ubuntu, kubuntu, xubuntu, even kali) - live disks - but get the same result. The drive shows in /dev/ as sdb - no sdb1, obviously partition is gone, however, it doesn't show in gparted at all. Here is a screenshot from thunar (same in nautilus, etc.)
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290654&d=1656319686[/IMG]
And here is the output from various commands:
lsusb before plugging in drive:
```
root@xubuntu:/home/xubuntu# lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2a Intel Corp. Bluetooth wireless interface
Bus 001 Device 004: ID 04f2:b573 Chicony Electronics Co., Ltd HD WebCam
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0951:1666 Kingston Technology DataTraveler 100 G3/G4/SE9 G2/50
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@xubuntu:/home/xubuntu#
```
lsusb after plugging in drive:
```
root@xubuntu:/home/xubuntu# lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2a Intel Corp. Bluetooth wireless interface
Bus 001 Device 004: ID 04f2:b573 Chicony Electronics Co., Ltd HD WebCam
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0951:1666 Kingston Technology DataTraveler 100 G3/G4/SE9 G2/50
Bus 001 Device 009: ID 058f:1234 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@xubuntu:/home/xubuntu#
```
fdisk:
```
root@xubuntu:/home/xubuntu# fdisk /dev/sdb

Welcome to fdisk (util-linux 2.36.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

fdisk: cannot open /dev/sdb: No medium found
root@xubuntu:/home/xubuntu#
```
The relevant part of dmesg:
```
[  161.078516] usb 1-1: new high-speed USB device number 6 using xhci_hcd
[  161.227804] usb 1-1: New USB device found, idVendor=048d, idProduct=1234, bcdDevice= 1.00
[  161.227842] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  161.227862] usb 1-1: Product: UDisk           
[  161.227877] usb 1-1: Manufacturer: General 
[  161.227892] usb 1-1: SerialNumber: &#1033;
[  161.235589] usb-storage 1-1:1.0: USB Mass Storage device detected
[  161.242219] scsi host1: usb-storage 1-1:1.0
[  162.267523] scsi 1:0:0:0: Direct-Access     General  UDisk            5.00 PQ: 0 ANSI: 2
[  162.269012] sd 1:0:0:0: Attached scsi generic sg1 type 0
[  162.270095] sd 1:0:0:0: [sdb] 61440000 512-byte logical blocks: (31.5 GB/29.3 GiB)
[  162.270933] sd 1:0:0:0: [sdb] Write Protect is off
[  162.270950] sd 1:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  162.274818] sd 1:0:0:0: [sdb] No Caching mode page found
[  162.274830] sd 1:0:0:0: [sdb] Assuming drive cache: write through
[  162.291239]  sdb:
[  162.292249] sd 1:0:0:0: [sdb] Attached SCSI removable disk
[  204.296225] usb 1-1: USB disconnect, device number 6
[  204.298355] blk_update_request: I/O error, dev sdb, sector 1 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0
[  204.298408] Buffer I/O error on dev sdb, logical block 1, lost async page write
[  204.298489] blk_update_request: I/O error, dev sdb, sector 30030 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0
[  204.298527] Buffer I/O error on dev sdb, logical block 30030, lost async page write
[  204.302677] blk_update_request: I/O error, dev sdb, sector 30032 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0
[  204.302728] Buffer I/O error on dev sdb, logical block 30032, lost async page write
[  204.302800] blk_update_request: I/O error, dev sdb, sector 30041 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0
[  204.302838] Buffer I/O error on dev sdb, logical block 30041, lost async page write
[  204.302950] blk_update_request: I/O error, dev sdb, sector 45352 op 0x1:(WRITE) flags 0x0 phys_seg 2 prio class 0
[  204.302988] Buffer I/O error on dev sdb, logical block 45352, lost async page write
[  204.303012] Buffer I/O error on dev sdb, logical block 45353, lost async page write
[  204.360465] FAT-fs (sdb): unable to read boot sector to mark fs as dirty
[  249.486754] usb 1-1: new high-speed USB device number 7 using xhci_hcd
[  249.825916] usb 1-1: New USB device found, idVendor=058f, idProduct=1234, bcdDevice= 0.01
[  249.825956] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  249.825976] usb 1-1: Product: Mass Storage Device
[  249.825992] usb 1-1: Manufacturer: Alcor Micro
[  249.836670] usb-storage 1-1:1.0: USB Mass Storage device detected
[  249.837373] scsi host1: usb-storage 1-1:1.0
[  250.844990] scsi 1:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 4
[  250.850753] sd 1:0:0:0: Attached scsi generic sg1 type 0
[  250.867291] sd 1:0:0:0: [sdb] Attached SCSI removable disk
[  504.398734] usb 1-1: USB disconnect, device number 7
[  568.974581] usb 1-1: new high-speed USB device number 8 using xhci_hcd
[  569.313762] usb 1-1: New USB device found, idVendor=058f, idProduct=1234, bcdDevice= 0.01
[  569.313801] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  569.313821] usb 1-1: Product: Mass Storage Device
[  569.313836] usb 1-1: Manufacturer: Alcor Micro
[  569.322407] usb-storage 1-1:1.0: USB Mass Storage device detected
[  569.323795] scsi host1: usb-storage 1-1:1.0
[  570.332605] scsi 1:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 4
[  570.337960] sd 1:0:0:0: Attached scsi generic sg1 type 0
[  570.359176] sd 1:0:0:0: [sdb] Attached SCSI removable disk
root@xubuntu:/home/xubuntu#
```
and dmesg | grep usb:
```
root@xubuntu:/home/xubuntu# dmesg | grep usb
[    0.227240] usbcore: registered new interface driver usbfs
[    0.227240] usbcore: registered new interface driver hub
[    0.227240] usbcore: registered new device driver usb
[    2.380923] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.11
[    2.380929] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.380932] usb usb1: Product: xHCI Host Controller
[    2.380935] usb usb1: Manufacturer: Linux 5.11.0-16-generic xhci-hcd
[    2.380938] usb usb1: SerialNumber: 0000:00:14.0
[    2.383960] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.11
[    2.383965] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.383969] usb usb2: Product: xHCI Host Controller
[    2.383971] usb usb2: Manufacturer: Linux 5.11.0-16-generic xhci-hcd
[    2.383974] usb usb2: SerialNumber: 0000:00:14.0
[    2.726196] usb 1-2: new high-speed USB device number 2 using xhci_hcd
[    2.876249] usb 1-2: New USB device found, idVendor=0951, idProduct=1666, bcdDevice= 1.10
[    2.876287] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.876306] usb 1-2: Product: DataTraveler 3.0
[    2.876320] usb 1-2: Manufacturer: Kingston
[    2.876333] usb 1-2: SerialNumber: 70C94E841688E321389D5F83
[    2.888504] usb-storage 1-2:1.0: USB Mass Storage device detected
[    2.889168] scsi host0: usb-storage 1-2:1.0
[    2.889358] usbcore: registered new interface driver usb-storage
[    2.892730] usbcore: registered new interface driver uas
[    3.006174] usb 1-3: new high-speed USB device number 3 using xhci_hcd
[    3.154922] usb 1-3: New USB device found, idVendor=0bda, idProduct=0129, bcdDevice=39.60
[    3.154936] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.154941] usb 1-3: Product: USB2.0-CRW
[    3.154946] usb 1-3: Manufacturer: Generic
[    3.154949] usb 1-3: SerialNumber: 20100201396000000
[    3.164842] usbcore: registered new interface driver rtsx_usb
[    3.282509] usb 1-4: new high-speed USB device number 4 using xhci_hcd
[    3.439652] usb 1-4: New USB device found, idVendor=04f2, idProduct=b573, bcdDevice=92.01
[    3.439691] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.439711] usb 1-4: Product: HD WebCam
[    3.439729] usb 1-4: Manufacturer: Chicony Electronics Co.,Ltd.
[    3.574500] usb 1-5: new full-speed USB device number 5 using xhci_hcd
[    3.725119] usb 1-5: New USB device found, idVendor=8087, idProduct=0a2a, bcdDevice= 0.01
[    3.725157] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   22.337688] usbcore: registered new interface driver btusb
[   22.691782] input: HD WebCam: HD WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input13
[   22.691952] usbcore: registered new interface driver uvcvideo
[  161.078516] usb 1-1: new high-speed USB device number 6 using xhci_hcd
[  161.227804] usb 1-1: New USB device found, idVendor=048d, idProduct=1234, bcdDevice= 1.00
[  161.227842] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  161.227862] usb 1-1: Product: UDisk           
[  161.227877] usb 1-1: Manufacturer: General 
[  161.227892] usb 1-1: SerialNumber: &#1033;
[  161.235589] usb-storage 1-1:1.0: USB Mass Storage device detected
[  161.242219] scsi host1: usb-storage 1-1:1.0
[  204.296225] usb 1-1: USB disconnect, device number 6
[  249.486754] usb 1-1: new high-speed USB device number 7 using xhci_hcd
[  249.825916] usb 1-1: New USB device found, idVendor=058f, idProduct=1234, bcdDevice= 0.01
[  249.825956] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  249.825976] usb 1-1: Product: Mass Storage Device
[  249.825992] usb 1-1: Manufacturer: Alcor Micro
[  249.836670] usb-storage 1-1:1.0: USB Mass Storage device detected
[  249.837373] scsi host1: usb-storage 1-1:1.0
[  504.398734] usb 1-1: USB disconnect, device number 7
[  568.974581] usb 1-1: new high-speed USB device number 8 using xhci_hcd
[  569.313762] usb 1-1: New USB device found, idVendor=058f, idProduct=1234, bcdDevice= 0.01
[  569.313801] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  569.313821] usb 1-1: Product: Mass Storage Device
[  569.313836] usb 1-1: Manufacturer: Alcor Micro
[  569.322407] usb-storage 1-1:1.0: USB Mass Storage device detected
[  569.323795] scsi host1: usb-storage 1-1:1.0
[  747.396101] usb 1-1: USB disconnect, device number 8
[  783.710658] usb 1-1: new high-speed USB device number 9 using xhci_hcd
[  784.049785] usb 1-1: New USB device found, idVendor=058f, idProduct=1234, bcdDevice= 0.01
[  784.049825] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  784.049846] usb 1-1: Product: Mass Storage Device
[  784.049861] usb 1-1: Manufacturer: Alcor Micro
[  784.060915] usb-storage 1-1:1.0: USB Mass Storage device detected
[  784.062738] scsi host1: usb-storage 1-1:1.0
root@xubuntu:/home/xubuntu#
```

Is this drive recoverable, or is it now a very expensive piece of nothing that was only used once?

---

### Post by sudodus on 2022-06-27
Try to use the tips in [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035) and bring your analysis further ahead.

It is possible that you will 'only' find that the USB flash drive is 'read-only' or 'dead', but I hope you will find a solution and make the drive work again.

Anyway, the drive is new, so if you find that it is dead, you should talk to the vendor and ask for a new one.

Edit: Please notice that USB flash drives are not recommended as backup media, because they are not reliable enough.

---

### Post by MimziM on 2022-07-19
Drive is dead, thanks - will contact vendor

---

