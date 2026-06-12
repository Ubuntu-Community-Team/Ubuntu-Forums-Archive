---
title: "Mount Samsung Note 8"
date: 2018-12-26
forum: General Help
---

### Post by Jason_Hunter on 2018-12-26
Whenever I plug my Note 8 into Ubuntu-18.04, it won't mount it. This used to work before. Now I only get: 

Dec 26 20:48:41 quasar kernel: [1237517.998574] usb 7-2: new high-speed USB device number 17 using xhci_hcd
Dec 26 20:48:41 quasar kernel: [1237518.153844] usb 7-2: New USB device found, idVendor=04e8, idProduct=6860, bcdDevice= 4.00
Dec 26 20:48:41 quasar kernel: [1237518.153846] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 26 20:48:41 quasar kernel: [1237518.153847] usb 7-2: Product: SAMSUNG_Android
Dec 26 20:48:41 quasar kernel: [1237518.153848] usb 7-2: Manufacturer: SAMSUNG
Dec 26 20:48:41 quasar kernel: [1237518.153849] usb 7-2: SerialNumber: ce061716dcb3490d027e
Dec 26 20:48:41 quasar kernel: [1237518.156332] cdc_acm 7-2:1.1: ttyACM0: USB ACM device
Dec 26 20:48:52 quasar kernel: [1237529.586754] cdc_acm 7-2:1.1: failed to set dtr/rts
Dec 26 20:48:52 quasar kernel: [1237529.587796] cdc_acm 7-2:1.1: failed to set dtr/rts
Dec 26 20:48:58 quasar kernel: [1237535.586967] cdc_acm 7-2:1.1: failed to set dtr/rts
Dec 26 20:49:29 quasar kernel: [1237566.202273] usb 7-2: USB disconnect, device number 17
Dec 26 20:49:32 quasar kernel: [1237569.775069] usb 7-2: new high-speed USB device number 18 using xhci_hcd
Dec 26 20:49:33 quasar kernel: [1237569.928127] usb 7-2: New USB device found, idVendor=04e8, idProduct=6860, bcdDevice= 4.00
Dec 26 20:49:33 quasar kernel: [1237569.928133] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 26 20:49:33 quasar kernel: [1237569.928137] usb 7-2: Product: SAMSUNG_Android
Dec 26 20:49:33 quasar kernel: [1237569.928141] usb 7-2: Manufacturer: SAMSUNG
Dec 26 20:49:33 quasar kernel: [1237569.928145] usb 7-2: SerialNumber: ce061716dcb3490d027e
Dec 26 20:49:33 quasar kernel: [1237569.932001] cdc_acm 7-2:1.1: ttyACM0: USB ACM device
Dec 26 20:49:36 quasar kernel: [1237573.674143] usb 7-2: USB disconnect, device number 18
Dec 26 20:49:36 quasar kernel: [1237573.674791] cdc_acm 7-2:1.1: failed to set dtr/rts
Dec 26 20:49:37 quasar kernel: [1237574.175101] usb 7-2: new high-speed USB device number 19 using xhci_hcd
Dec 26 20:49:37 quasar kernel: [1237574.328033] usb 7-2: New USB device found, idVendor=04e8, idProduct=6860, bcdDevice= 4.00
Dec 26 20:49:37 quasar kernel: [1237574.328035] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 26 20:49:37 quasar kernel: [1237574.328036] usb 7-2: Product: SAMSUNG_Android
Dec 26 20:49:37 quasar kernel: [1237574.328037] usb 7-2: Manufacturer: SAMSUNG
Dec 26 20:49:37 quasar kernel: [1237574.328038] usb 7-2: SerialNumber: ce061716dcb3490d027e
Dec 26 20:49:37 quasar kernel: [1237574.330513] cdc_acm 7-2:1.1: ttyACM0: USB ACM device

---

