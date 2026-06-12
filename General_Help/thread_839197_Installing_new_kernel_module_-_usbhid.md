---
title: "Installing new kernel module - usbhid"
date: 2008-06-24
forum: General Help
---

### Post by sultanoswing on 2008-06-24
I've compiled a new kernel module, usbhid.ko, which I need for support for a force feedback device (Thrustmaster Dual Power 3).

What's the best way of properly installing this module to run at startup?

I have a usb keyboard, so whenever I 'sudo rmmod usbhid' I can no longer enter the required 'sudo insmod usbhid'. I did copy and overwrite the usbhid.ko found in /lib/modules/2.6.24-19-generic/kernel/drivers/hid with my newly compiled module, but am not sure this is the proper way or whether the new module is in fact working (the force feedback certainly isn't).

Any scripts or alternate methods would be much appreciated!

---

### Post by Mikecore on 2008-06-24
> **sultanoswing said:**
> I've compiled a new kernel module, usbhid.ko, which I need for support for a force feedback device (Thrustmaster Dual Power 3).

What's the best way of properly installing this module to run at startup?

I have a usb keyboard, so whenever I 'sudo rmmod usbhid' I can no longer enter the required 'sudo insmod usbhid'. I did copy and overwrite the usbhid.ko found in /lib/modules/2.6.24-19-generic/kernel/drivers/hid with my newly compiled module, but am not sure this is the proper way or whether the new module is in fact working (the force feedback certainly isn't).

Any scripts or alternate methods would be much appreciated!

```

sudo rmmod usbhid && sudo insmod usbhid 

```

or 

```

sudo rmmod usbhid && sudo modprobe usbhid

```

either should work

---

### Post by wdaniels on 2008-06-25
> **sultanoswing said:**
> What's the best way of properly installing this module to run at startup?

Use /etc/modules file to load a module at startup and /etc/modprobe.d/blacklist to prevent a module from loading.

---

### Post by sultanoswing on 2008-06-25
> **wdaniels said:**
> Use /etc/modules file to load a module at startup and /etc/modprobe.d/blacklist to prevent a module from loading.

Thanks for the help, guys. 

What if the blacklisted module is the same name as the one I want to load i.e. usbhid? I suppose the one I want to load is at a different location i.e. /home/username/usbhid.ko

Trying the first suggestion (sudo rmmod hid && insmod /home/username/usbhid.ko gave the error: -1 Unknown symbol in module

Hmmmmm!?

---

### Post by Mikecore on 2008-06-28
> **sultanoswing said:**
> Thanks for the help, guys. 

What if the blacklisted module is the same name as the one I want to load i.e. usbhid? I suppose the one I want to load is at a different location i.e. /home/username/usbhid.ko

Trying the first suggestion (sudo rmmod hid && insmod /home/username/usbhid.ko gave the error: -1 Unknown symbol in module

Hmmmmm!?

sounds like you have an error with the module.

---

