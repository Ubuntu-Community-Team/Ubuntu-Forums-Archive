---
title: "Mount flash drive at usb 1.1"
date: 2007-10-30
forum: General Help
---

### Post by Christobevii3 on 2007-10-30
I would like to use my flash drive with vmware windows xp for a vb class I have.  What is the mount option i can set under the properties and settings to set it to usb 1.1.  Thanks

---

### Post by cdenley on 2007-10-30
I don't think there is such a mount option since the device is initialized when it is connected, before it is mounted. However, I think you can disable the USB 2.0 driver before it is connected to force it to use USB 1.1. Make sure you don't have any USB 2.0 devices connected before running this command.

```

sudo modprobe -r ehci-hcd

```

---

