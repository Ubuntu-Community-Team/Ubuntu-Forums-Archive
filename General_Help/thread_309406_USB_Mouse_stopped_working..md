---
title: "USB Mouse stopped working."
date: 2006-11-29
forum: General Help
---

### Post by Scythe!? on 2006-11-29
Hi, I booted into Ubuntu today after not using it for ages and the USB mouse does not get any power. This mouse works in windows btw. The mouse is a razor copperhead. Any ideas?

---

### Post by Henry Rayker on 2006-11-29
Just to clarify: the mouse worked before you stopped using Ubuntu?

It could be a driver issue...I'm not familiar with the mouse (I know it's a gaming mouse, but outside of that, I don't know much...) Does the mouse require drivers in windows?

Does it show up with an lsusb? (I believe something should show up that way)

---

### Post by Scythe!? on 2006-11-29
> **Henry Rayker said:**
> Just to clarify: the mouse worked before you stopped using Ubuntu?

It could be a driver issue...I'm not familiar with the mouse (I know it's a gaming mouse, but outside of that, I don't know much...) Does the mouse require drivers in windows?

Does it show up with an lsusb? (I believe something should show up that way)

Yes it worked in Ubuntu perfectly before, now there is no power at all

EDIT: lsusb displays:
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

The mouse has power at the very start of the boot up screen, then disappears.

---

### Post by mgmiller on 2006-11-29
With intermittent USB mouse issues, what has worked for me is to go into the BIOS in the machine and find the "enable legacy USB" entry and disable it.

---

### Post by Scythe!? on 2006-11-30
> **mgmiller said:**
> With intermittent USB mouse issues, what has worked for me is to go into the BIOS in the machine and find the "enable legacy USB" entry and disable it.

Cant find that. When linux is booted, when i take out my mouse and put it back in, a small amount of power is used on the mouse, then it switches off in about 0.5 seconds.

---

### Post by Henry Rayker on 2006-11-30
Do you know if those USB ports are actually functioning at all in Ubuntu? Could you try another peripheral, if you have one?

---

### Post by Eddy Dean on 2006-11-30
I'm sometimes having the same problem with my Logitech Trackball, but logging in again sometimes helps. I'm not sure if that's the same problem then you have.
The "normal" mouse that's connected to the PS/2 port works fine at all times.


Greetz,
Eddy Dean

---

### Post by Scythe!? on 2006-11-30
Got it working now. I just restored a xorg.conf file and it was ok, yet nothing had changed in the xorg.conf file. :confused:

---

### Post by Henry Rayker on 2006-11-30
huh...that is kind of weird. Maybe there was just a little difference...it's easy to glance over those.

I'm glad you got it working, though!

---

