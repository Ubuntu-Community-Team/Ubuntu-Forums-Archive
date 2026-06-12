---
title: "Samsung SCH-i760 shows up as eth1"
date: 2008-05-02
forum: General Help
---

### Post by brandt on 2008-05-02
Hi all,
I just got a Samsung SCH-i760 and have been checking out options on the forums for how to sync and transfer files to it.  When I connect it to my computer, however, it looks like the computer is assigning it to eth1 rather than treating it like a mass-storage device.

dmesg output:
```

[ 5475.009843] usb 1-2: new full speed USB device using ohci_hcd and address 18
[ 5476.584601] usb 1-2: configuration #1 chosen from 1 choice
[ 5476.658196] eth1: register 'rndis_host' at usb-0000:00:02.0-2, RNDIS device, 80:00:60:0f:e8:00

```

Any clue how to get around this?  Thanks.
-Brandt

---

