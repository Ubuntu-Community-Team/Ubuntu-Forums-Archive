---
title: "Error -110 on a powered USB port?"
date: 2015-04-10
forum: General Help
---

### Post by jasonditz on 2015-04-10
The computer in question was assembled about 18 months ago, no hardware changes since. This morning I started getting multiple errors of this variety during boot:

usb 6-5: device descriptor read/64, error -110

So that's not a really uncommon error (first time on this system though), -110 means the device is trying to draw more power than the USB can provide. Usual fix is to unplug everything USB for a couple mins to let it reset. I did all that, and while there were fewer instances of that error this time on boot, it recurred. Then I realized something:

usb 6-5 is the multicard reader part of my Rosewill RDCR-11004. That device is a 2.0 hub, a 3.0 hub, a multicard reader, and a eSata. It's also got a 4-pin connection directly to the PSU. 

The error only appears a handful of times during boot, always 6-5, before the system declares "usb usb6-port5: unable to enumerate USB device." The device then pops up at 8-5 without the error and appears to function as normal. 6-1 through 6-4 are the USB 2.0 hub inside the Rosewill, and all those ports are functioning as expected as well. 

So questions: what does all this mean, and should I worry about the -110 error when it only appears during boot, and doesn't appear to be impacting the functionality of anything? Again, nothing on this system is new, and everything was playing well with others for the past 18 months.

---

