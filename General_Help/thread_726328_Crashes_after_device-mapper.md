---
title: "Crashes after device-mapper"
date: 2008-03-16
forum: General Help
---

### Post by Locuss on 2008-03-16
During bootup, my computer fails to completely boot, and restarts. Booting up with knoppix, and checking /var/log/dmesg, I see that the last entry is 

device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]

Its the last entry for the last several failed boots as well, so it seems to be the constant factor in the crashes.
Any ideas whats going wrong?

My kernel is the stock 2.6.22-generic, and I'm using Ubuntu Gutsy 7.10, on this hardware

500 GB sata2 drive,
AMD Athlon 5600+ X2
Nvidia 7300 SE
Anything else needed?

---

### Post by Locuss on 2008-03-16
Ran a western digital diagnostic tool... read element error code 007.

---

