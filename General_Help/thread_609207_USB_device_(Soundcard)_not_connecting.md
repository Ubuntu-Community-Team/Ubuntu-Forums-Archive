---
title: "USB device (Soundcard) not connecting"
date: 2007-11-10
forum: General Help
---

### Post by Face1 on 2007-11-10
When I used to plug in my usb soundcard (or on windows), the device "turns on":  the light on it turns on, and the speakers pop.  Now this is not happening, and I have no idea why.  Below is the dmesg output when I plug it in:```
[ 5845.368000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 5845.664000] usb 1-1: configuration #1 chosen from 1 choice
[ 5845.668000] cannot find the slot for index 0 (range 0-0), error: -16
[ 5845.668000] cannot create card instance 0
[ 5845.668000] snd-usb-audio: probe of 1-1:1.0 failed with error -5
```

How can I fix this?

---

