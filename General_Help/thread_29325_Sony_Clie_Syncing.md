---
title: "Sony Clie Syncing"
date: 2005-04-23
forum: General Help
---

### Post by cobranmu on 2005-04-23
Hey Everyone,

Looking for someone single looking for a good time. Nope, just kidding.

Having some issues syncing my clie with evolution. I've done the following:

1) Created a sym link from /dev/ttyUSB1 to /dev/pilot along with chmod 777 on pilot
2) I've been able to get the Username and UID off the pilot using the function built into Gnome Pilot.
3) First time I tried to copy the initial data to evolution, it worked, since then, nothing syncs.

Any thoughts?

---

### Post by Laurent Cazalet on 2005-04-24
is the /dev/pilot link still here? it doesn't remain across reboots. You must recreate it at boot. 
or simply use /dev/ttyUSB1 as device for your clié.

If you know what you're doing, it's a better solution to create a short udev rule. 
 I've got a handspring visor. here my /etc/udev/rules.d/visor.rule:
```
BUS="usb",  KERNEL="ttyUSB1", SYSFS{product}="Handspring Visor", SYMLINK="visor"B
```

---

