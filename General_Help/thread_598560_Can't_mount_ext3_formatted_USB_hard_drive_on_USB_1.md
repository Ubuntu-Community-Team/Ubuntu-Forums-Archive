---
title: "Can't mount ext3 formatted USB hard drive on USB 1.1 port"
date: 2007-10-31
forum: General Help
---

### Post by Old Pink on 2007-10-31
I get an error like> reset high speed USB device using uchi_hcd

On the desktop (USB 2.0) I get > reset high speed USB device using echi_hcd and merely using ```
sudo modprobe -r ehci_hcd
```solves this wheras on the 1.1 laptop ```
sudo modprobe -r ehci_hcd
```and```
sudo modprobe -r uhci_hcd
```do very little. 

Any suggestions? :)

---

### Post by timcredible on 2007-10-31
if the external hard drive is usb 2.0, you shouldn't need to do anything to have it connect to a usb 2.0 port.  i have an usb 2.0 external hard drive with a fat32 and an ext3 partition, it auto-mounts no problem.  if you're having issues with that, the drive may have a problem.

---

