---
title: "Seperating USB devices"
date: 2008-01-03
forum: General Help
---

### Post by adam.tropics on 2008-01-03
So I have an iPod (which works fine!), a Canon camera, which work fine, and an external drive that works fine! All are USB, and rarely is more than one plugged in at a time.

In the interest of separating the way they are recognized, are evdev rules the way to go? I have been using different fstab entries for the iPod and external drive, since they use different filesystems, but that has caused 'confused' mount points from time to time. Given that only one is in at a time, it is always sda1, is it ok to have more than one fstab rule for sda1?(surely not!) And finally the camera has just always worked. I only mention it, since it too is usb, and I haven't touched a single setting with regard to it!

So what I want to do, is to have the 3 devices recognized for which device they actually are, mounted to an appropriate place etc etc. I think I am just over complicating it in my mind, so anyone know any good guides to help me clean this up a bit?

---

### Post by dcstar on 2008-01-04
> **adam.tropics said:**
> So I have an iPod (which works fine!), a Canon camera, which work fine, and an external drive that works fine! All are USB, and rarely is more than one plugged in at a time.

In the interest of separating the way they are recognized, are evdev rules the way to go? I have been using different fstab entries for the iPod and external drive, since they use different filesystems, but that has caused 'confused' mount points from time to time. Given that only one is in at a time, it is always sda1, is it ok to have more than one fstab rule for sda1?(surely not!) And finally the camera has just always worked. I only mention it, since it too is usb, and I haven't touched a single setting with regard to it!

So what I want to do, is to have the 3 devices recognized for which device they actually are, mounted to an appropriate place etc etc. I think I am just over complicating it in my mind, so anyone know any good guides to help me clean this up a bit?

Label the partitions and they will be mounted with the label names (do a forum search for instructions on labelling each type of partition).

---

