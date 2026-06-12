---
title: "UVC video device, PLEASE HELP!  :)"
date: 2006-12-10
forum: General Help
---

### Post by rainbowjoshua on 2006-12-10
Hello!

So I am trying to get working my "Logitech Quickcam Fusion", which is listed on the uvc video site as supported.  I downloaded, compiled and installed the uvc drivers, with no hitches or errors.  Now, when I plug the device in I get:

```
[17188058.384000] usb 3-2: new high speed USB device using ehci_hcd and address 5
[17188063.708000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[17188064.008000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.
[17188064.008000] uvcvideo: Failed to initialize the device (-5).
[17188065.008000] 5:3:1: cannot set freq 0 to ep 0x86

```

I don't know what to try next.  Any ideas?  Thanks all!  Running Dapper.

Cheers! Joshua

---

### Post by rainbowjoshua on 2006-12-11
So after redownloading and recompling the uvc driver again, the device now shows up, and ekiga sees it and tries to use it, however, gets an error and dmesg generates the following error:

```
uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
```

I've only found other people who've had this problem and no solutions.  Please, any ideas or leads would be so appreciated!

Thanks,
Joshua

---

### Post by whatalotta on 2006-12-11
Having the same issue here.  Tried compiling the gspcav driver but that fails saying config.h is missing.  I have the Logitech Quickcam Orbit.

Anyone have any ideas?

-Whata

---

