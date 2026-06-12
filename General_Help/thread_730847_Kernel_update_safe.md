---
title: "Kernel update safe?"
date: 2008-03-21
forum: General Help
---

### Post by StewD on 2008-03-21
Hi

I have a Belkin Switch2 (switches the Keyboard/Monitor/Mouse/Audio between two PCs), which works well with Linux and Windows.

However, I would like to use the software to allow independent audio switching, and Belkin only support Windows for this.

I've found a Linux equivalent called flapjack ([http://sourceharvest.com/](http://sourceharvest.com/)). This states that " the kernel must be altered to force hiddev device creation for the Belkin Flip KVM"

and continues:

```
A patch to do this, which applies against the 2.6.20.4 kernel, is in the 
file doc/flapjack-kernel-2.6.20.4.patch. Apply it with the following commands:

     $ cp doc/flapjack-kernel-2.6.20.4.patch /tmp
     (root)# cd /usr/src/linux
     (root)# patch -p1 </tmp/flapjack-kernel-2.6.20.4.patch

Replace the "/usr/src/linux" with the location of your linux source code. 
After applying the patch, rebuild and reinstall the kernel and reboot or reload the 
usbhid module
```.

This is a bit beyond my comfort zone, so would appreciate some advice and guidance!

(I am running the latest fully patched version of Ubuntu)

1. Is it safe to follow these instructions and run the patch in?
2. for the second line do I change to cd /usr/src/linux-headers-2.6.22-14 ?
3. How do I rebuild and reinstall the kernel? This sounds dangerous!!
4. What effect will this change have on future Ubuntu patches/upgrades?

Or is there an alternative way to achieve "hiddev device creation" what ever that means!

Many thanks for any advice on any of this!

Stew

---

### Post by Sef on 2008-03-21
**Back up** your data first.  There is no guarantees that all will go 100%.

---

