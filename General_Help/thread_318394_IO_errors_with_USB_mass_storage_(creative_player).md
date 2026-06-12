---
title: "IO errors with USB mass storage (creative player)"
date: 2006-12-13
forum: General Help
---

### Post by bricedebrignaisplage on 2006-12-13
I have a creative MP3 player (id: HD-0015). It can be set as  a USB mass storage of some size (500MB, 1GB, ... up to 20GB), currently 2GB. It worked well under Dapper, but stopped working after I upgraded to Edgy: when I try to write on it, it hangs and finally reports an IO error and gets deconnected. One of my friend who is using Mandriva and kernel 2.6.17 has the same issue.

I know it's a know issue, and used to be reported a lot at first, but it seems to have disappeared from forums. So I am wondering if I had missed a fix or workaround. At first I expected a new kernel release to fix it within a few days, but it's been a while now...

Anybody knows about any way to fix that?
Is it a kernel problem with 2.6.17?

---

### Post by luopio on 2006-12-18
Yo. I'm having the same problem. I get this in dmesg:
```
[17184076.892000] usb 4-1: new high speed USB device using ehci_hcd and address 14
[17184077.004000] usb 4-1: device descriptor read/64, error -71
```

Practically happens with my canon 350d and one usb stick. My usb hardrive does work on the other hand.. and my usb sound card. It might be related to problems with the ehci-hcd module (usb 2.0 devices) although I'm not sure... Thinking about compiling my own kernel to get it working once and for all.

[EDIT] Tested with a few different scenarios and now I'm beginning to think the problem is related to my USB-port (which doubles as a firewire port). The usb stick won't work when connected to it, but it will work when connected to the usb-dongle that is connected to an usb 2.0 port. And ehci-hcd is used when I connect it, so the kernel module seems to work ok (except for firewire/usb-ports) [/EDIT]

---

