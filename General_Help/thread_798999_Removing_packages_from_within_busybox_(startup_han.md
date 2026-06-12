---
title: "Removing packages from within busybox (startup hang after new packages installed)"
date: 2008-05-18
forum: General Help
---

### Post by Afromonkey0 on 2008-05-18
Hi,

I'm a complete ubuntu noob, though i was pretty good with windows. In a fit of joy at how damn easy 'apt-get install' is for adding new packages, i went and added about 10 before rebooting, like an idiot. Now ubuntu will not boot, and shows this as the last few lines when i boot in verbose mode (or whatever it's called)

input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard Hub on usb-0000:00:1d.1-2.1
usbcore: registered new interface driver usbhid
/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

This is Hardy Heron installed with Wubi on a Dell machine. Stuff I installed, if I remember correctly, a bunch of python modules, blutooth drivers, and I think also amarok media player, though that may have been earlier.
I have a hunch it's the bluetooth, because the bluetooth USB dongle is plugged into the USB port on my keyboard, and it hangs on USB-HID.

So, is there a way that I can get rid of whatever is causing the problem from within the inramfs(?) it drops me into if I press return at the hang? The normal terminal commands don't work.
If not, what else can I do?

Thanks in advance :)
- Afromonkey0

P.S You guys have got an incredible OS here, I've had no compatibility problems and the thing out 'wow's vista even on my old PC. No graphics card and not a frame of lag, CPU barely ticking over, just incredible.

---

### Post by ago on 2008-05-18
It depends when the hang happens. Normally the command is:

sudo apt-get remove PKG-NAME

---

### Post by Afromonkey0 on 2008-05-18
> **ago said:**
> It depends when the hang happens. Normally the command is:

sudo apt-get remove PKG-NAME

I get
/bin/sh: sudo: not found

Like I said, the normal commands don't work. Is there another way?

Thanks though, quick response.

Edit: without sudo it says
/bin/sh: apt-get: not found

---

### Post by ago on 2008-05-18
That means that you are still in the initrd when it hangs. Try to boot in rescue mode (press esc at boot after "ubuntu")

---

### Post by Afromonkey0 on 2008-05-18
> **ago said:**
> That means that you are still in the initrd when it hangs. Try to boot in rescue mode (press esc at boot after "ubuntu")

That's my bad, I forgot to say I'm in rescue mode already. In normal mode I just get a blank screen.
What do I do in rescue mode?

---

### Post by MountainX on 2009-02-26
did you find any solution?

---

### Post by Afromonkey0 on 2009-02-27
It works now, though this problem was a really long time ago and I can't remember how i fixed it. I may have just reinstalled the whole OS.

Sorry i can't be of more help.

---

