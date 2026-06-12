---
title: "USB key oddities, if its in on boot everything is good, if not..."
date: 2006-12-06
forum: General Help
---

### Post by Devilotx on 2006-12-06
So here is an oddity I've encounterd with my laptop and Edgy,

If I boot my laptop with a Key insterted, upon boot, there is an icon on the desktop pointing to either /media/ANKH or /media/GIGKEY depending on which key I had in,  I can right click the icon, and eject it, reinstert it, insert the other key and everything works just ducky.

However...

If I book without the USB key inserted, inserting the key does nothing, no mount, no file system, nothing.  it's very odd.  I get odd errors in the /var/log/messages file

Dec  6 11:36:33 horus kernel: [17189104.816000] usb 2-2: new high speed USB device using ehci_hcd and address 17
Dec  6 11:37:36 horus kernel: [17189167.232000] usb 2-2: new high speed USB device using ehci_hcd and address 18
Dec  6 11:37:47 horus kernel: [17189178.904000] usb 2-2: new high speed USB device using ehci_hcd and address 19
Dec  6 11:37:59 horus kernel: [17189190.576000] usb 2-2: new high speed USB device using ehci_hcd and address 20
Dec  6 11:38:10 horus kernel: [17189201.124000] usb 2-2: new high speed USB device using ehci_hcd and address 21
Dec  6 11:41:20 horus kernel: [17189391.336000] usb 2-2: new high speed USB device using ehci_hcd and address 22
Dec  6 11:41:31 horus kernel: [17189402.996000] usb 2-2: new high speed USB device using ehci_hcd and address 23
Dec  6 11:41:43 horus kernel: [17189414.680000] usb 2-2: new high speed USB device using ehci_hcd and address 24
Dec  6 11:41:54 horus kernel: [17189425.236000] usb 2-2: new high speed USB device using ehci_hcd and address 25
Dec  6 11:43:17 horus kernel: [17189508.228000] usb 2-2: new high speed USB device using ehci_hcd and address 26
Dec  6 11:43:28 horus kernel: [17189519.900000] usb 2-2: new high speed USB device using ehci_hcd and address 27
Dec  6 11:43:40 horus kernel: [17189531.560000] usb 2-2: new high speed USB device using ehci_hcd and address 28
Dec  6 11:43:51 horus kernel: [17189542.096000] usb 2-2: new high speed USB device using ehci_hcd and address 29

But in the end, no mount, no good...

any advice?

---

### Post by Devilotx on 2006-12-06
Noticed that /dev/sdb doesn't appear in /dev/ when I don't boot with a key in,  and it doesn't show up when a key is inserted, this must be the issue. but how to fix it?

---

