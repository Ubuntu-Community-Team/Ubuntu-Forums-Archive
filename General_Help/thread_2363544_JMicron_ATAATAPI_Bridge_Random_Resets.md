---
title: "JMicron ATA/ATAPI Bridge Random Resets"
date: 2017-06-11
forum: General Help
---

### Post by lotharmat on 2017-06-11
I have a HDD enclosure that I connect to my laptop via a USB3 port.

Initially the hard disk works fine but then freezes and the following appears in dmesg:

[ +0.040256] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 4 ep 2 with no TDs queued?
[Jun11 11:42] usb 4-3: reset SuperSpeed USB device number 5 using xhci_hcd
[Jun11 11:43] usb 4-3: reset SuperSpeed USB device number 5 using xhci_hcd

This keeps happening.

If I plug the same enclosure into a USB2 port - all is fine albeit slower.

It doesn't matter what HDD I have in the enclosure - I get the same errors.


I have added 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend_delay_ms=-1" 
```

to /etc/default/grub

I have added 

```
options usb-storage quirks=0x152d:0x0569:u
options usbcore autosuspend=-1
options usbcore autosuspend_delay_ms=-1

```

to /etc/modprobe.d/usb3-disk-bug.conf

All to no avail.

If I use a Sabrent cable that connects to the HDD it works perfectly.

---

### Post by lotharmat on 2017-06-13
Apologies - Realised my question is missing:

Does anyone else get this behaviour with the JMicron ATA/ATAPI bridge and USB3 (XHCI_hcd Driver)?

---

