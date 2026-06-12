---
title: "Drivers messed something up"
date: 2007-03-10
forum: General Help
---

### Post by jabooty on 2007-03-10
In an effort to get my webcam to work, I installed the spca5xx drivers via automatix.  Now, when I try to import photos from my digital camera, I get an error stating:

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I guess all I need to do is uninstall the drivers I just installed.  The question is: how do I do that?

---

### Post by taurus on 2007-03-10
If you use Automatix to install it, you can use Automatix to uninstall it.  Fire up Automatix and you should see it in the uninstall window.

---

### Post by jabooty on 2007-03-10
Automatix says:
> Uninstallation of spca5xx modules is not supported.  Reinstallation of the same from Automatix will be safe.

So, in other words, it won't uninstall the drivers.  Any suggestions?

---

### Post by jackrobinson on 2007-03-10
try this:
```
sudo modprobe -r spca5xx
```

---

### Post by jabooty on 2007-03-10
Same problem.  Oy... what did I break?!

---

### Post by jackrobinson on 2007-03-10
> **jabooty said:**
> Same problem.  Oy... what did I break?!

The above command unloaded the spca5xx module which is apparently hogging your camera. Unplug the camera, restart the computer and plug it back in.

---

### Post by jabooty on 2007-03-11
I ran modprobe -r spca5xx and it removed the driver.

When I reboot, it loads again, and I get the same error.

---

### Post by jabooty on 2007-03-12
Any ideas?

---

### Post by jabooty on 2007-03-13
Bump.  I figured this would be an easy fix.  Surely someone has an idea.

---

### Post by jabooty on 2007-03-16
I keep hoping someone will see this and know an answer.

---

