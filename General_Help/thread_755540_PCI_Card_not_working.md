---
title: "PCI Card not working"
date: 2008-04-14
forum: General Help
---

### Post by dldeskins on 2008-04-14
Hello,

I have an old server on which I installed Ubuntu 7.10.  I added a USB PCI card to add 4 USB 2.0 ports.  I had to remove an extra network card that I wasn't using.  Now the card is recognized but nothing shows up when I plug in a USB device.  Any suggestions?

Thanks,
Don

---

### Post by geraldm on 2008-04-15
Check that the usb modules are loaded.   
The command lsmod should report ehci_hcd, uhci_hcd and ohci_hcd

Gerald

---

### Post by dldeskins on 2008-04-15
Gerald, 

Thanks for your reply.

When I did a lsmod,itreported that ohci_hcd, but ehci_hcd and uhci_hcd did not.  What do I do now?  BTW, I have 2 usb drives working off a usb 1.1 port with a hub right now.  I would like to get the USB 2 going simply because it is faster.

Thanks,

Don

---

### Post by dldeskins on 2008-04-15
Gerald, you gave me just enough to get me going. :)

I edited /etc/modules (added ehci_hcd, uhci_hcd and ohci_hcd) and rebooted.  My usb 2 PCI card is now working.

---

