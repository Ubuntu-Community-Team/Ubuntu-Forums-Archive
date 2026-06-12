---
title: "Trying to Import Photos from Sakar Camera"
date: 2008-01-05
forum: General Help
---

### Post by Jamie Jackson on 2008-01-05
I've got a Sakar 25290 ("Hotshot") camera, from which I'm trying to import photos into Xubuntu 7.10. I thought it would automount as a USB drive when I plugged it in, but no luck.

I tried to use it from gtkam, but this model of Sakar is not listed. I tried using all the other Sakar models, each with all three USB settings, but it didn't recognize the device (no surprise).

Please let me know if you have any ideas.

I don't know if any of the following helps, but here goes.

When I unplug it and plug it back in, dmesg reports this sort of thing ```
[169848.192000] usb 1-2: USB disconnect, address 5
[169849.944000] usb 1-2: new full speed USB device using uhci_hcd and address 6
[169850.176000] usb 1-2: configuration #1 chosen from 1 choice

```

...and if I diff an ls of /dev/ before and after I plug it in, I get:

```
diff dev1.txt dev2.txt 
1a2
> 1-2
665a667,671
> usbdev1.5_ep00
> usbdev1.5_ep01
> usbdev1.5_ep03
> usbdev1.5_ep82
> usbdev1.5_ep84

```

---

### Post by Jamie Jackson on 2008-01-06
I posted an [enhancement request]("https://sourceforge.net/tracker/?func=detail&atid=358874&aid=1864801&group_id=8874") to gphoto to support this camera, but I'm still interested in a workaround, since it could be a while...

---

