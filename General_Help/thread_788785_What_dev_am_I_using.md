---
title: "What /dev am I using?"
date: 2008-05-10
forum: General Help
---

### Post by pacrep on 2008-05-10
I am trying to get lcdproc to work with my Palm Tx using Palmorb. The problem Is I don't know
what /dev/ I'm using so I can use lcdproc on my palm. 

Hotsync uses,
Using gnome-pilot Setting: -> Devices Tab.

Devices: ```
usb:
```



lsusb:
```
Bus 004 Device 062: ID 0830:0061 Palm, Inc.
```

dmesg:
```
[18695.364309] usb 4-1: new full speed USB device using uhci_hcd and address 67
[18695.533300] usb 4-1: configuration #1 chosen from 1 choice.
```


lshal --monitor:
```
22:24:25.253: usb_device_830_61_PN70U8Q6V1M8 added
22:24:25.316: usb_device_830_61_PN70U8Q6V1M8_if0 added

```

So how can I map the device I'm using for lcdproc? Please help.

---

