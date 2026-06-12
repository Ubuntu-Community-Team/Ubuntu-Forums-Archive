---
title: "Is there a way to emulate a usb device?"
date: 2008-07-07
forum: General Help
---

### Post by mriedel on 2008-07-07
Dunno if this is the right place to post it, couldn't really decide.

Anyway I was wondering whether there is a way to, say, create two partitions on a usb device, one of which is encrypted with cryptsetup/LUKS and then fool the system into believing the encrypted one is a standalone usb device after *cryptsetup luksOpen*'ing it without the decrypted partition being mounted anywhere.

In simpler terms I want /dev/mapper/sdX_crypt to appear as a (fake) usb device.

Ideally hotplugging would still work so that when I unplug the actual usb device (which will be used read-only), the mapper device disappears (making the system believe the fake usb device was just unplugged).

---

### Post by mriedel on 2008-07-08
bump

---

