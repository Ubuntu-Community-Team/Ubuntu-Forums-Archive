---
title: "Help getting htc excalibur / tmobile Dash working with synce rndis-lite"
date: 2007-08-26
forum: General Help
---

### Post by AhronZombi on 2007-08-26
hello. ive been trying for 2 days to get my htc Excalibur to work with the rndis-lite drivers according to the synce wiki and other guides ive looked at in the ubuntu forum. ive recompiled my kernel as specified and compiled the lite driver but my computer still onlt sees my device as generic serial and not a rndis device. if anyone knows of a good guide for me to look at or if you have advice for me please assist

when i connect the device with the rndis_host module loaded i still get this and it dosent create a rndis0 device
```
[ 2154.044000] usb 1-2: new full speed USB device using ohci_hcd and address 5
[ 2154.268000] PM: Adding info for usb:1-2
[ 2154.268000] PM: Adding info for No Bus:usbdev1.5_ep00
[ 2154.268000] usb 1-2: configuration #1 chosen from 1 choice
[ 2154.272000] PM: Adding info for usb:1-2:1.0
[ 2154.272000] PM: Adding info for No Bus:usbdev1.5_ep81
[ 2154.272000] PM: Adding info for No Bus:usbdev1.5_ep02
[ 2154.272000] PM: Adding info for No Bus:usbdev1.5

```

---

