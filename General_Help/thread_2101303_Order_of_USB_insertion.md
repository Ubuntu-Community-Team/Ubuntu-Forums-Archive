---
title: "Order of USB insertion"
date: 2013-01-04
forum: General Help
---

### Post by coyoteboy on 2013-01-04
Hi all,

Been a long time but I'm looking for some advice, I hope someone can help me out. I've got a couple of products that are USB communications items (jtag programmers) and the software that is using them requires them to be inserted in a fixed order. I cannot change this software, it's closed source. 

The problem is that the computer gets updated and rebooted fairly frequently (I try to minimise it) and as the USB items are left in the sockets, ubuntu re-initialises them in the wrong order (seemingly randomly?) so the order gets lost and the items stop functioning. The computer is a laptop but it's being used remotely for now so it's a bit of a pain.

So the question is:
Is there a way of fixing the order in which the items are initialised? I'm not 100% sure exactly what I want to fix as the USB items have their PID and VID fixed, it's obviously some sort of mapping that goes astray?

Any help would be greatly appreciated.

---

### Post by Grenage on 2013-01-04
I assume this is down to the mount names? I.E: ttyusb0, ttyusb1.

Or is it the devices themselves that need to initialise in a set order?

---

### Post by coyoteboy on 2013-01-04
> **Grenage said:**
> I assume this is down to the mount names? I.E: ttyusb0, ttyusb1.

Or is it the devices themselves that need to initialise in a set order?

I think it's down to the mount points as you say, rather than the units themselves - I think they're not aware of each other so shouldn't matter. I'm going to go and double check that in the next hour or so.

---

### Post by Grenage on 2013-01-04
A couple of years ago I needed to be able to plug in a USB stick, and have it automatically copy files from a directory; this naturally required knowing where the stick was mounted.

I ended up writing a udev rule, which lets you run a command when a device with a particular ID (or other criteria) is connected.  That allowed me to ensure that a device was always mounted in the same place.  An option, perhaps?

---

