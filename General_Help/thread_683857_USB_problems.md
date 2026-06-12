---
title: "USB problems"
date: 2008-01-31
forum: General Help
---

### Post by paradoxni on 2008-01-31
Gutsy 64bit / 2.6.22-14-generic

Im having some USB device problems, especially after the device has been disconnected and then reconnected.

The devices work fine when first plugged in / PC turned on, however not if they are unmounted / remounted.

2 recent examples:

If I unmount my IPOD and then try and remount it, it will not be detected, the LED on my usb hub will flicker and then go off. I must unplug the IPOD and reconnect to a different port on the USB hub to get it to work again, which is mildly annoying.

If I turn on my printer it will be detected and print fine, however if I turn it off again and then back on it will not be detected the second time, unless I reboot the PC (changing usb ports does not fix this one).

Both examples above give similar error messages in DMESG:

```

[ 8555.247473] usb 3-6: new high speed USB device using ehci_hcd and address 50
[ 8555.379675] usb 3-6: configuration #1 chosen from 1 choice
[ 8555.379744] hub 3-6:1.0: USB hub found
[ 8555.379851] hub 3-6:1.0: 7 ports detected
[ 8555.687092] usb 3-6.3: new high speed USB device using ehci_hcd and address 51
[ 8555.759046] usb 3-6.3: device descriptor read/64, error -71
[ 8555.938814] usb 3-6.3: device descriptor read/64, error -71
[ 8556.114627] usb 3-6.3: new high speed USB device using ehci_hcd and address 52
[ 8556.186582] usb 3-6.3: device descriptor read/64, error -71
[ 8556.362394] usb 3-6.3: device descriptor read/64, error -71
[ 8556.538207] usb 3-6.3: new high speed USB device using ehci_hcd and address 53
[ 8556.941712] usb 3-6.3: device not accepting address 53, error -71
[ 8557.013713] usb 3-6.3: new high speed USB device using ehci_hcd and address 54
[ 8557.417218] usb 3-6.3: device not accepting address 54, error -71
[ 8557.613104] usb 3-6.5: new full speed USB device using ehci_hcd and address 55

```

---

