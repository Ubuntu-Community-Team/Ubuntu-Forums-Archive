---
title: "UBUNTU CRASH! drmI810 wait_ring error!  How to install a &quot;.so&quot; driver?"
date: 2007-02-07
forum: General Help
---

### Post by emarkay on 2007-02-07
The error message is (as best as I could copy it down)"

"DRM I810 wait_ring.....65520 wanted 65528..."

Of course most posts have a I830 instead of an I810 error (I have an Intel 82810E On- Board Graphics card, but they all reference iomething about the XFree86 drivers....

Here is the [apparent patch]
i810_drv.so
[https://bugs.freedesktop.org/show_bug.cgi?id=5774](https://bugs.freedesktop.org/show_bug.cgi?id=5774)

Here's one of the Launchpad bugs:
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/28326](https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/28326)

So HOW DO I GET THIS PATCH INSTALLED INTO MY UBUNTU?

THANK YOU!

---

### Post by emarkay on 2007-02-08
Help!   Anyone?

---

### Post by emarkay on 2007-02-08
Resolved by reconfiguring xorg.

---

