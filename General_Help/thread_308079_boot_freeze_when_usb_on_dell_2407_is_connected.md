---
title: "boot freeze when usb on dell 2407 is connected"
date: 2006-11-27
forum: General Help
---

### Post by djsamsel on 2006-11-27
if i plug the usb hub built into my dell 2407 monitor into a usb port, the boot process stops at these two lines

17179583-26400 ohci_hcd 0000:00:0b.0: OHCI Host Controller
17179583-26400 ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1

this monitor replaced a dell 1905 that had a usb hub and ran with no problems. the only difference is the 2407 has a built in memory card reader as well. 

if i unplug the usb on the monitor ubuntu boots fine. any suggestions? thanks in advance for the help. doug

---

### Post by Ancistrus on 2006-12-29
*bump*

djsamsel,  I am having exactly the same problem.  Did you ever manage to solve this.

From some further reading I did find that I could manage to boot by disabling legacy USB devices in BIOS settings.  There must be a better solution.

Thanks in advance for any suggestions.

---

