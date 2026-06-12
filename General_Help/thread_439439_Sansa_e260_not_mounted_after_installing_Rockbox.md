---
title: "Sansa e260 not mounted after installing Rockbox"
date: 2007-05-10
forum: General Help
---

### Post by jbm222 on 2007-05-10
I just installed Rockbox on my Sansa e260.  Before installing rockbox, it would automatically show up on my desktop.  Now I can't get it to show up at all.  Any ideas?

dmesg gives the following right after plugging it in:

```
[ 2139.460000] usb 4-5: new high speed USB device using ehci_hcd and address 31
[ 2140.572000] usb 4-5: device descriptor read/64, error -71
[ 2145.024000] usb 4-5: new high speed USB device using ehci_hcd and address 32
[ 2146.136000] usb 4-5: device descriptor read/64, error -71

```

[b]
nevermind.  I found my answer.  apparently rockbox doesn't support USB on the Sansa e200 series yet.  So I have to reboot into the original firmware which is done by holding the "left" key.  Sorry.[/b]

---

