---
title: "Possible regression in camera access"
date: 2014-06-21
forum: General Help
---

### Post by PaulBx on 2014-06-21
I have a Canon ELPH 330 HS. I used to use PCManFM to transfer the jpg's over to the hard drive, or maybe "cp" in a console window. I can no longer do that.

Now when the camera mounts, the directory I am copying from appears in PCManFM like "gphoto2://[usb:003,004]/DCIM/105___06". I don't believe it used to look like that. The message when "cp" fails indicates it cannot find it. When I try right-clicking a file in PCManFM on the camera, it does not give the usual context menu (with "copy", "cut" and "paste" among other things).

I can still double-left click a file there and it opens the usual jpg viewer. Then within that, I can save the file to the hard drive, but doing it that way, one photo at a time, is tedious.

---

### Post by PaulBx on 2014-06-21
Oh, I am still on 13.10 by the way, but it should be up to date. I can't say when the change happened, but I think it is within the last month or so.

---

### Post by PaulBx on 2014-07-04
I found my new Kindle does the same thing, showing up like "mtp://[usb:003,004]/" rather than a more conventional directory name under /media, the way it used to be mounted. Anybody have an idea what is going on? This makes file access and maintenance on my devices very difficult.

---

### Post by PaulBx on 2014-07-04
I found this about using gmtp:
[http://www.linuxandlife.com/2013/01/Kindle-Fire-HD-Linux-recognize.html](http://www.linuxandlife.com/2013/01/Kindle-Fire-HD-Linux-recognize.html)
[http://android.stackexchange.com/questions/38304/how-do-i-mount-a-kindle-fire-10-2-6-on-my-linux-computer](http://android.stackexchange.com/questions/38304/how-do-i-mount-a-kindle-fire-10-2-6-on-my-linux-computer)

I installed it and tried it on the Kindle; however when I do "connect" in that window, gmtp freezes.

Here is what dmesg says:
```

[87894.165402] usb 3-2: new high-speed USB device number 5 using xhci_hcd
[87894.187898] usb 3-2: New USB device found, idVendor=1949, idProduct=000b
[87894.187907] usb 3-2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[87894.187911] usb 3-2: Product: Kindle
[87894.187915] usb 3-2: Manufacturer: Amazon
[87894.187918] usb 3-2: SerialNumber: 00D20708352203VS
[88148.122453] usb 3-2: usbfs: process 17258 (gmtp) did not claim interface 0 before use
[88148.287715] usb 3-2: reset high-speed USB device number 5 using xhci_hcd
[88148.309660] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a62d26c0
[88148.309669] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a62d2700
[88148.309674] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a62d2740
[88148.315163] usb 3-2: usbfs: process 17258 (gmtp) did not claim interface 0 before use
[88148.315228] usb 3-2: usbfs: process 17141 (events) did not claim interface 0 before use
[88148.315346] usb 3-2: usbfs: process 17141 (events) did not claim interface 0 before use
[88215.403586] usb 3-2: usbfs: process 17264 (pool) did not claim interface 0 before use
[88227.900373] usb 3-2: USB disconnect, device number 5
[88236.433433] usb 3-2: new high-speed USB device number 6 using xhci_hcd
[88236.456037] usb 3-2: New USB device found, idVendor=1949, idProduct=000b
[88236.456045] usb 3-2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[88236.456050] usb 3-2: Product: Kindle
[88236.456053] usb 3-2: Manufacturer: Amazon
[88236.456057] usb 3-2: SerialNumber: 00D20708352203VS
[88267.641979] usb 3-2: usbfs: process 17284 (gmtp) did not claim interface 0 before use
[88267.809084] usb 3-2: reset high-speed USB device number 6 using xhci_hcd
[88267.831136] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a4339780
[88267.831145] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a43397c0
[88267.831150] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a4339800
[88267.836644] usb 3-2: usbfs: process 17284 (gmtp) did not claim interface 0 before use
[88267.836709] usb 3-2: usbfs: process 17282 (events) did not claim interface 0 before use
[88308.164961] usb 3-2: usbfs: process 17289 (pool) did not claim interface 0 before use
[88333.503300] usb 3-2: USB disconnect, device number 6

```

---

### Post by PaulBx on 2014-07-04
Woops, I found that I also needed to install mtpfs. Now I can transfer files using gmtp to the Kindle.

I guess for the camera I will just remove the card to make the transfer.

---

