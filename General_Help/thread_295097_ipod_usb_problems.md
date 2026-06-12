---
title: "ipod usb problems"
date: 2006-11-07
forum: General Help
---

### Post by danielph on 2006-11-07
RESOLVED

Hi, 

I have some problems after an ipod firmware change with a manual install of ipodlinux that got interupted before completion.

The status is this:
ipod has permanant apple
windows cannot see it
hp format util cannot see it
itunes cannot see it
ipod reset just restarts in same state
Linux can see the usb device and this is where I am now.

tail /var/log/messages:
```
Nov  7 21:25:05 morocco kernel: [17222245.476000] ohci_hcd 0000:00:03.1: wakeup
Nov  7 21:25:05 morocco kernel: [17222245.860000] usb 2-1: new full speed USB device using ohci_hcd and address 95
Nov  7 21:25:06 morocco kernel: [17222246.612000] usb 2-1: new full speed USB device using ohci_hcd and address 96
Nov  7 21:25:07 morocco kernel: [17222247.364000] usb 2-1: new full speed USB device using ohci_hcd and address 97
Nov  7 21:25:07 morocco kernel: [17222247.948000] usb 2-1: new full speed USB device using ohci_hcd and address 98
```ls -l /dev | grep sd  - fails to show any sd devices



The question is, how can I access this usb device and get it back to a state where I can rebuild it. I need to be able to mount it once more.

thanks for reading this far

---

### Post by danielph on 2006-11-07
This was an ipod issue. It was stuck in a loop and reseting did not clear it. A key sequence, reboot (hold on, hold off, hold down menu and play) followed immediately by holding rew and fwd after it reboots. This put it into disk mode and I am now able to access it.

---

