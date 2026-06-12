---
title: "How To Download Images from BlackBerry?"
date: 2007-12-22
forum: General Help
---

### Post by SuperMike on 2007-12-22
I have Fiesty 7.04 and a BlackBerry Curve 8310. Does anyone have a Perl script to download image data from it? I looked at Barry but I have no idea how to install it in the right sequence of dependencies and so on.

---

### Post by DoctorMO on 2007-12-24
Barry won't be able to download your images anyway, it's a syncing tool that integrates with the pim information (for now)

Your best bet is to get a mini sd card and put that in the phone, then linux will see it as a usb file system and mount it. put your images on the sd card from the blackberry options page.

---

### Post by maclenin on 2007-12-31
**DoctorMO:**

Do you know whether there is a way to mount the blackberry without the mini sd card? I have made an attempt to do so - (in 7.04) - and my laptop sees the blackberry, is able to identify it...

```
[128471.824000] sd 1:0:0:0: Attached scsi removable disk sdb
[128471.824000] sd 1:0:0:0: Attached scsi generic sg1 type 0
```

...but will not complete the (auto) mount process. Maybe there is a manual/fstab-related mount solution? Or, is the mini sd the "only" way?

Thanks.

---

