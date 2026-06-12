---
title: "usb trouble - hardy vs. gutsy"
date: 2008-07-02
forum: General Help
---

### Post by chochem on 2008-07-02
Since upgrading to hardy I'd been having all kinds of problems with usb connections so after trying everything from kernel boot parameters, loading and unloading modules, upgrading & downgrading kernels, changing file managers and even switching desktop environments, I finally just reinstalled gutsy and the usb problems are gone (I think/hope - hardy would almost inevitably have choked on the 20 Gb file transfer I just completed). 

To be more specific: Hardy would at some seemingly random point in a transfer drop the high-speed connection  and then reconnect the device using 'full speed' (about 1 Mb/s) if at all. Once the transfer was complete, the connection would typically go completely and I would have to restart in order to reconnect the device.

So my question is: Can anyone tell me exactly what I should ascribe the difference to? The kernel difference? The usb modules? (I believe they are mutually dependent and they're both currently pinned at 2.6.22-14) And if so should I be able to retain proper usb functioning with a 2.6.22-14 kernel in Hardy? Running Gutsy these days means compiling an awful lot of software yourself...

---

