---
title: "[solved] usb failure after recent package update"
date: 2008-07-06
forum: General Help
---

### Post by checksum_101 on 2008-07-06
If your usb is working ignore this

Around two or so package updates ago i lost all USB functionality.
After along time down the rabbit hole I found out:

sudo rmmod ehci_hcd

worked, but no more USB 2.0

Fix for now:
edit your /etc/rc.local 

and add:
echo 1 > /sys/module/usbcore/parameters/old_scheme_first
above the line:
exit 0

---

