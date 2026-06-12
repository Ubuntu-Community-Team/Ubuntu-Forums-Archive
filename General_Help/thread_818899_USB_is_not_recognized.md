---
title: "USB is not recognized"
date: 2008-06-04
forum: General Help
---

### Post by sombrancelha on 2008-06-04
Hi,

I'm having a problem.

I'm using Hardy and I've got all updates installed. This problem started happening when I installed Hardy, it didn't happen in Gutsy.

Well, let's go to it. When the computer is on and I plug any USB device (pendrive, mouse, etc.), it is not recognized by the system. It's not simply that it's not being mounted, the computer just doesn't recognize that there's a pendrive in the USB port. (However, I'm not 100% sure that's indeed happening, though I'm pretty sure).

If I want to use any USB device, I have to turn the computer on with the device already plugged. Then it works fine.

Any idea on what's going on and how to solve it?
Thanks in advance.

---

### Post by Prospero2006 on 2008-06-04
First thing I'd do:
Plug in the usb device after the machine is turned on.
```

dmesg

```
The last few lines should indicate a usb connection of some sort.
If not, it's not recognizing anything plugged in.
In that case, I'd revert to an earlier kernel and try that again to compare results.

Also try this:
```

rmmod usbhid
modprobe usbhid

```
If you have a usb keyboard or mouse, that will disable them.
It should return error free otherwise.

Just some suggestions

---

### Post by sombrancelha on 2008-06-08
After
```
dmesg
```
I get
```
[  149.045629] [<f88aab80>] (usb_hcd_irq+0x0/0x60 [usbcore])
```
After
```
rmmod usbhid
```
I get
```
ERROR: Module usbhid does not exist in /proc/modules
```
For 
```
modprobe usbhid
```
I had to run with sudo, and I got no messages.

What does that errors mean?

I tried to go to an earlier kernel, and it worked. However, all video configurations were messed up. I had to come back to my current kernel and it was quite a problem to reset everything. So I'd rather stay with the current kernel, if that's possible.

---

