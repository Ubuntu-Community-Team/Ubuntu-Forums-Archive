---
title: "Is anyone using a 2.4ghz wireless (not wifi) usb camera with linux?"
date: 2007-07-08
forum: General Help
---

### Post by harty83 on 2007-07-08
I bought a First Alert 550 which is a 2.4ghz camera with a usb receiver.   I'm trying to get it to work with linux but so far no luck.

lsusb lists it as:
```
Bus 006 Device 006: ID eb1a:2861 eMPIA Technology, Inc.
```

When I do a "ls /dev" when it is plugged in and when it is not then compare them, I have an audio1, dsp1, and mixer1 which is correct because it has a built in mic.  There is also listed
```
usbdev6.4_ep00
usbdev6.4_ep81
usbdev6.4_ep82
usbdev6.4_ep83
usbdev6.4_ep84
```
when it is plugged in.  But none of them will work via zm, xawtv, or camorama.  

I guess this is a driver issue.  Any clue what I can do?

Thanks!

---

