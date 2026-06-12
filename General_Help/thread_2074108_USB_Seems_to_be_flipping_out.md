---
title: "USB Seems to be flipping out"
date: 2012-10-21
forum: General Help
---

### Post by sloggerkhan on 2012-10-21
When I boot USB devices don't work for minutes and I see a lot of errors like the ones below in my syslog:
```

Oct 20 21:22:00 *********** kernel: [  439.359433] usb 1-1.4: device descriptor read/64, error -110
Oct 20 21:22:15 *********** kernel: [  454.528355] usb 1-1.4: device descriptor read/64, error -110
Oct 20 21:22:15 *********** kernel: [  454.704183] usb 1-1.4: new high-speed USB device number 9 using ehci_hcd
Oct 20 21:22:30 *********** kernel: [  469.769075] usb 1-1.4: device descriptor read/64, error -110
Oct 20 21:22:45 *********** kernel: [  484.938004] usb 1-1.4: device descriptor read/64, error -110
Oct 20 21:22:46 *********** kernel: [  485.113958] usb 1-1.4: new high-speed USB device number 10 using ehci_hcd
Oct 20 21:22:56 *********** kernel: [  495.516869] usb 1-1.4: device not accepting address 10, error -110
Oct 20 21:22:56 *********** kernel: [  495.588967] usb 1-1.4: new high-speed USB device number 11 using ehci_hcd
Oct 20 21:23:06 *********** kernel: [  505.991944] usb 1-1.4: device not accepting address 11, error -110
Oct 20 21:23:06 *********** kernel: [  505.992066] hub 1-1:1.0: unable to enumerate USB device on port 4

```

Eventually devices seem to recognize for the most part, though not always.

I'm experimenting with reinstalling various things, but just thought I'd ask. Related, I also had to repair my bootloader after the recent updates. So maybe related. Not sure.

Oh, and all my USB ports are 2.0 or 3.0, so not sure about that, either.

---

