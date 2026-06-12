---
title: "CF card usb2 usb3 port"
date: 2014-03-24
forum: General Help
---

### Post by spacemen12 on 2014-03-24
Hi,
    I have a CF card (sanDisk extreme 8gb 60Mb/s) that is behaving badly. It cannot mount when plug in a usb3 port. It sometimes work when plus on older usb port, but it often timeout and disappear. When mounted correctly, I tried F3 ([http://oss.digirati.com.br/f3/](http://oss.digirati.com.br/f3/)), I was able to write it all, but it was unable to read it back because of "Buffer I/O error on device", usually before 1gb was read.

    Those behaviors are the same after I format the card in camera (there is no issue with the card while in the camera), or after I format it in the computer. 

    I have another card of the same brand and type and it does work perfectly (so I assume it is not the wire or the card reader, camera, computer, etc.). 

Tried it on a ubuntu 13.10 and ubuntu 12.04 and with multiple computers with the same behavior.

I did run badblocks on it while plug in and there is nothing wrong, but it often unplug itself before badblocks finishes.

Below is the dmesg when I plug it to an old usb (successful) and usb3 (unsuccesful)

old usb
```

> [17094.472236] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
> [17094.566237] usb 1-1.3: New USB device found, idVendor=058f, idProduct=6366
> [17094.566244] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
> [17094.566248] usb 1-1.3: Product: Mass Storage Device
> [17094.566251] usb 1-1.3: Manufacturer: Generic
> [17094.566254] usb 1-1.3: SerialNumber: 058F0O1111B1
> [17094.566901] scsi16 : usb-storage 1-1.3:1.0
> [17095.565048] scsi 16:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
> [17095.566560] sd 16:0:0:0: Attached scsi generic sg5 type 0
> [17095.740231] usb 1-1.3: reset high-speed USB device number 3 using ehci-pci
> [17096.384375] sd 16:0:0:0: [sdf] 15625216 512-byte logical blocks: (8.00 GB/7.45 GiB)
> [17096.385492] sd 16:0:0:0: [sdf] Write Protect is off
> [17096.385499] sd 16:0:0:0: [sdf] Mode Sense: 03 00 00 00
> [17096.386609] sd 16:0:0:0: [sdf] No Caching mode page found
> [17096.386617] sd 16:0:0:0: [sdf] Assuming drive cache: write through
> [17096.390481] sd 16:0:0:0: [sdf] No Caching mode page found
> [17096.390488] sd 16:0:0:0: [sdf] Assuming drive cache: write through
> [17096.415109]  sdf: unknown partition table
> [17096.418581] sd 16:0:0:0: [sdf] No Caching mode page found
> [17096.418588] sd 16:0:0:0: [sdf] Assuming drive cache: write through
> [17096.418593] sd 16:0:0:0: [sdf] Attached SCSI removable disk
> [17096.568540] EXT4-fs (sdf): mounted filesystem with ordered data mode. Opts: (null)

```


usb3
```
> [16922.132114] usb 3-1: new high-speed USB device number 2 using xhci_hcd
> [16922.151906] usb 3-1: New USB device found, idVendor=058f, idProduct=6366
> [16922.151913] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
> [16922.151917] usb 3-1: Product: Mass Storage Device
> [16922.151921] usb 3-1: Manufacturer: Generic
> [16922.151924] usb 3-1: SerialNumber: 058F0O1111B1
> [16922.153007] scsi13 : usb-storage 3-1:1.0
> [16923.153102] scsi 13:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
> [16923.154608] sd 13:0:0:0: Attached scsi generic sg5 type 0
> [16923.364538] usb 3-1: reset high-speed USB device number 2 using xhci_hcd
> [16923.382059] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8810180ab500
> [16923.382066] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8810180ab540
> [16923.600612] usb 3-1: reset high-speed USB device number 2 using xhci_hcd
> [16923.618134] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8810180ab500
> [16923.618141] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8810180ab540
> [16923.836554] usb 3-1: reset high-speed USB device number 2 using xhci_hcd
> [16923.854086] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8810180ab500
> [16923.854093] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8810180ab540
...
> [16928.786190] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8810180ab540
> [16928.786971] sd 13:0:0:0: [sdf] READ CAPACITY failed
> [16928.786977] sd 13:0:0:0: [sdf]  
> [16928.786980] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
> [16928.786984] sd 13:0:0:0: [sdf] Sense not available.
> [16928.996587] usb 3-1: reset high-speed USB device number 2 using xhci_hcd
> [16929.014124] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8810180ab500
> [16929.014131] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8810180ab540

```



What do you suggest to save this CF card?

---

### Post by spacemen12 on 2014-03-25
If I disable xhci in the BIOS, it works no problem. 

What worries me is that the weir behavior is only for one card out of two "identical" (same spec, brand, model, size) CF card.

I would like to understand.

---

