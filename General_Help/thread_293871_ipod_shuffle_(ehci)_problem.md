---
title: "ipod shuffle (ehci) problem"
date: 2006-11-05
forum: General Help
---

### Post by deldredge on 2006-11-05
Hi,
I'm having problems with my 2 ipod shuffles, one 1g and one 2g. I'll also mention that this setup works fine with my regular 5g ipod.

My shuffle won't mount in ubuntu unless I disable ehci, which causes it to transfer at usb 1.1 speeds, which sucks! Also, I have to unload the ehci module every time I restart ubuntu, which also sucks. I want to see if there is something else I can do, but I'm not very savvy with this kind of problem. Here is the dmeg output I get when I plug in my shuffle without previously unloading ehci:

```
[17189066.268000] usb 4-4: new high speed USB device using ehci_hcd and address 4
[17189071.400000] usb 4-4: unable to read config index 0 descriptor/start
[17189071.400000] usb 4-4: can't read configurations, error -110
[17189071.512000] usb 4-4: new high speed USB device using ehci_hcd and address 5
[17189076.644000] usb 4-4: unable to read config index 0 descriptor/start
[17189076.644000] usb 4-4: can't read configurations, error -110
[17189076.756000] usb 4-4: new high speed USB device using ehci_hcd and address 6
[17189081.776000] usb 4-4: device descriptor read/all, error -110
[17189081.888000] usb 4-4: new high speed USB device using ehci_hcd and address 7
[17189086.908000] usb 4-4: device descriptor read/all, error -110
[17189088.192000] usb 4-4: new high speed USB device using ehci_hcd and address 8
[17189088.304000] usb 4-4: device descriptor read/64, error -71
[17189093.544000] usb 4-4: unable to read config index 0 descriptor/start
[17189093.544000] usb 4-4: can't read configurations, error -110
[17189093.660000] usb 4-4: new high speed USB device using ehci_hcd and address 9
[17189098.808000] usb 4-4: unable to read config index 0 descriptor/start
[17189098.808000] usb 4-4: can't read configurations, error -110
[17189098.924000] usb 4-4: new high speed USB device using ehci_hcd and address 10
[17189103.952000] usb 4-4: device descriptor read/all, error -110
[17189104.064000] usb 4-4: new high speed USB device using ehci_hcd and address 11

```

Can anyone help? I don't understand why a regular ipod will work fine, but a new shuffle (with a dock) doesn't work! I'm going nuts!

---

