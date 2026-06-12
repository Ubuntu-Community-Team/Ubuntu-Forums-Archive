---
title: "Samsung camera via USB"
date: 2015-11-01
forum: General Help
---

### Post by ELMIT on 2015-11-01
After connecting the Samsung camera, which has a 32G SD card dmesg shows:

> [1645221.295490] usb 3-7: reset high-speed USB device number 37 using xhci_hcd
[1645221.425931] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803309140c0
[1645221.425935] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880330914108
[1645273.875067] usb 3-7: USB disconnect, device number 37
[1645274.145696] usb 3-7: new high-speed USB device number 38 using xhci_hcd
[1645274.279516] usb 3-7: New USB device found, idVendor=04e8, idProduct=1389
[1645274.279518] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[1645274.279520] usb 3-7: Product: Samsung Digital Camera
[1645274.279521] usb 3-7: Manufacturer: SAMSUNG Electronics Co., Ltd.
[1645274.279522] usb 3-7: SerialNumber: 000000000001
[1645274.281220] usb-storage 3-7:1.0: USB Mass Storage device detected
[1645274.281278] scsi22 : usb-storage 3-7:1.0


How can I access the data?

---

### Post by Bucky Ball on 2015-11-01
You mean the camera is not appearing on the desktop or in a file manager?

---

### Post by Geoffrey_Arndt on 2015-11-02
Have you tried putting just the SD card in the built-in PC card reader (or an external one which are quite inexpensive)?

---

### Post by sudodus on 2015-11-02
What is the output of the following command?

```
sudo lsblk -fm
```

If the camera's SD card is not recognized as a mass storage device (for example /dev/sdb), you may have better luck with a photo organizer program, for example **shotwell** or **digikam**. These programs have a feature to import data from cameras, even if they are not recognized as mass storage devices.

---

