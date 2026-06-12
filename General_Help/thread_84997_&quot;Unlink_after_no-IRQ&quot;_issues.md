---
title: "&quot;Unlink after no-IRQ&quot; issues"
date: 2005-11-01
forum: General Help
---

### Post by anjiro on 2005-11-01
I just installed Breezy on a new machine, and I'm getting these messages when I insert a USB2 memory stick:

usb 3-1: new high speed USB device using ehci_hcd and address 4
ehci_hcd 0000:00:0c.2: Unlink after no-IRQ? Controller is probably using the wrong IRQ.
usb 3-1: device not accepting address 4, error -110
usb 3-1: new high speed USB device using ehci_hcd and address 5
usb 3-1: device not accepting address 5, error -110
usb 3-1: new high speed USB device using ehci_hcd and address 6
usb 3-1: device not accepting address 6, error -110

...and so on. I saw a suggesting that passing "noapic" to the kernel would fix this, but no luck. Anyone have any ideas?

Update: passing "acpi=off" fixes this, but it's not really a good solution.


Thanks,


dan

---

### Post by wickwire on 2006-02-14
Try booting the kernel with "irqpoll" as described [here]("http://www.ubuntuforums.org/showthread.php?t=81153&highlight=noapic+usb")

---

