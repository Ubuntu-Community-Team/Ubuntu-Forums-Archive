---
title: "Block usb device loading as cdrom"
date: 2018-04-06
forum: General Help
---

### Post by yetimon_64 on 2018-04-06
Hi everyone,

I have a ZTE mobile wireless device I connect to the internet through, that occasionally I need to power directly from a usb port. When I do this the device registers and automatically mounts as a cdrom (with windows drivers etc on it).

The device, from "lsusb"...
```
Bus 001 Device 009: ID 19d2:1405 ZTE WCDMA Technologies MSM
```

Whether the device is plugged into the mains power or the usb ports it works fine, ie. there is no problem with connecting to the internet through it from either power source.

I would however like to block the device registering as a cd rom device with my ubuntu install (14.04). The install is built up from a minimal image and has several DEs installed, currently running xfce while attempting this. I mention this only as this is not what could be considered a "standard installation" (though I don't think that should affect this particular task, just to mention such conditions exist).

I have tried setting a udev rule to block the device loading after doing a bit of preliminary research on google. What I tried was setting up a "/etc/udev/rules.d/99-hide.rules" file which included the contents...
```
SUBSYSTEM=="usb_device", ATTR{idVentor}=="19d2", ATTR{idProduct}=="1405",ENV{UDISKS_PRESENTATION_HIDE}:="1"
```... which unfortunately doesn't seem to do anything; the device keeps mounting as a cdrom.

Anyone know how to block the device loading as a cdrom drive when plugged into the usb port for power only needs?

Cheers, yeti.

---

### Post by yetimon_64 on 2018-04-08
bump

---

### Post by sudodus on 2018-04-08
What is the problem with the device loading as a cdrom drive? Just that it is cluttering the desktop (and the output of some commands)? Or is it causing some more severe problem?

If only cluttering, maybe this link can help:

[Stop cluttering the desktop](https://help.ubuntu.com/community/mkusb#Stop_cluttering_the_desktop)

---

### Post by yetimon_64 on 2018-04-08
No severe problems more just a constant nuisance with it popping up in the file manager and also with notifications all for a drive full of windows only software.

I tend to hide my many partitions from the file manager with drive flags etc and this cd rom keeps popping up in the file manager side window (nautilus by the way is in use on xfce, this is pretty much a hybrid install of quite a few DEs).

No problem with the desktop itself as I have all drives and icons turned off for xfdesktop in the xfce settings utility (pretty much as is shown in your link).

I regularly turn off the device when not actually using it and when it is turned on again the cd rom pops up again and gives a notification as it does so. A niggling minor annoyance that I'd love to stop at the source as it can happen many times a day.
[B]
Edit[/B]: I may have just found a workaround, I'm currently using i3 tiling window manager (no DE) and tried turning the device off and on again. No notifications occurred and the device though showing in nautilus didn't automatically mount, a better outcome than on xfce or unity etc.

---

### Post by sudodus on 2018-04-08
I don't know how to do it, but I think it is possible to blacklist a device. If that is possible also in this case, I hope someone who knows will chip in and help you :-P

Otherwise, if the i3 tiling window manager can do what you need, fine :-)

---

### Post by yetimon_64 on 2018-04-08
Well it turns out there was a simpler method than blocking the device at the hardware level as I've been trying to do ](*,). I finally found a setting in "Removable drives and media" > "Storage tab" that stopped the automatic mounting and notifications. The setting that needed deselecting is "mount removable media when inserted".

 The device still registers in the side pane of nautilus but doesn't automatically mount or spam me with a notification now. Which is good enough to stop the constant nuisance and can be easily reverted if I need to use the cd/dvd drive of the laptop.

No more need to handicap the hardware now :smile:. Marking this as solved. 

@ sudodus, thanks for the assistance.

Cheers, yeti.

---

### Post by sudodus on 2018-04-09
I'm glad you found a good solution. Thanks for sharing it :-)

---

