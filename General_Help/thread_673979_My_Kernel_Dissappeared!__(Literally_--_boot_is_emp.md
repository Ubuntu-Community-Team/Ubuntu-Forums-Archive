---
title: "My Kernel Dissappeared!  (Literally -- /boot is empty)"
date: 2008-01-21
forum: General Help
---

### Post by TrompeLaMort on 2008-01-21
Hi,

I've got a *really* strange problem.  My version of kUbuntu no longer has any kernels in /boot

I was trying to upgrade my kernel to include the USB modules necessary to look under /proc/usb and see what was plugged in (I couldn't figure out what port my palm pilot was plugged into).

So I went to the package manager, and looked up the USB package.  I forget what it was called -- usbsomething.

Since I was installing modules, I rebooted my computer to load them (I wasn't sure what ??insmod?? command to use to load them).

My computer didn't load.  Grub still worked, but it couldn't access Linux. 

So I got out my ubuntu CD and booted into a shell prompt.  I figured maybe the name of my kernel had changed.

Unfortunately /boot is empty.  It contains /boot/grub and /boot/memtest but no kernels.

So:

a)  How do I get a kernel I can throw in /boot and use with grub
b)  What log can I look in to figure out what the hell happened?
c)  Is this some kind of bug I should report because it pretty much seems like a show stopper?

Thanks,

Dan

---

