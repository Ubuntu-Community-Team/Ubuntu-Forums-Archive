---
title: "Changing load order of kernel modules"
date: 2007-12-28
forum: General Help
---

### Post by Peter__v on 2007-12-28
I have a problem with usb because the load order of ehci_hcd and uhci-hcd are in wrong order. First is loaded uhci-hcd and then ehci_hcd.

This causes errors like:

usb 5-1: device not accepting address 12, error -110

So the solution is removing uhci-hcd and ehci-hcd with modprobe -r and then loading first ehci-hcd and then uhci-hcd.

But how to make this permanent? That would be better :)

---

### Post by Peter__v on 2007-12-28
hmm what i did now to solve the problem:

sudo mv /lib/modules/2.6.22-14-generic/kernel/drivers/usb/host/ehci-hcd.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/host/ehci-hcd.ko.bu

dont think it can get nastier as that :guitar:

---

### Post by Peter__v on 2007-12-28
what the... it still loaded ehci-hcd

mouse stopped working after a couple minuts waiting and after i plugged it out and in. 

and after i did sudo modprobe -r ehci_hcd  it started working again:mad:

So my idea has changed i want to completely remove ehci_hcd.i tried to blacklist it in 

/etc/modprobe.d/blacklist

and still it loaded.....:confused:

---

