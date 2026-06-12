---
title: "External HD enclosure not detected..."
date: 2008-07-04
forum: General Help
---

### Post by erikschneider21 on 2008-07-04
I bought an external HD enclosure for a desktop drive, and Ubuntu Hardy won't detect it. I've Googled for some answers and so far, no luck.

It doesn't show up in fdisk -l, or anywhere else for that matter.

This is the system log when I plug it in:
```
Jul  4 15:08:57 eu kernel: [  140.177743] usb 6-4: new high speed USB device using ehci_hcd and address 5
Jul  4 15:08:58 eu kernel: [  140.213636] usb 6-4: config 1 has an invalid interface number: 2 but max is 1
Jul  4 15:08:58 eu kernel: [  140.213648] usb 6-4: config 1 has no interface number 1
Jul  4 15:08:58 eu kernel: [  140.215378] usb 6-4: configuration #1 chosen from 1 choice
Jul  4 15:08:58 eu kernel: [  140.217231] hiddev96hidraw0: USB HID v1.10 Device [Cypress AT2LP RC42] on usb-0000:00:1a.7-4
```

I'm not sure what to do. I would really like this to work with Ubuntu.

Thanks,

Erik

---

