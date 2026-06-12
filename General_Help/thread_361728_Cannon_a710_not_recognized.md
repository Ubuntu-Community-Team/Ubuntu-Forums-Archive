---
title: "Cannon a710 not recognized"
date: 2007-02-14
forum: General Help
---

### Post by z987k on 2007-02-14
I'm having trouble importing photo's from my a710.  It's simply plugged in via usb, so I would have figured it would just show up as a mass storage device if nothing else, which I'm fine with.  Or an import app like gphoto that pops up when I plug in the camera.  However neither work.  It doesn't seem to automount or anything like that and gphoto gives this error message:  
```

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
```

Now I found a possible workaround - [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)
 but this doesn't work either.  

Has anyone had any success with the 710 or from what I've been reading cannons in general?

---

### Post by batholith on 2007-02-14
I got around a lot of the "driver" issues by just buying a cheap ($13) internal "All in one" card reader.  It reads SD, XD, CF, and numerous other formats and you don't have to download directly from the camera.  Actually it's a lot faster reading directly from the card...and it mounts just like a flash drive or similar device...

---

### Post by z987k on 2007-02-15
I don't understand why you would need a driver for a usb camera.  You would think it would mount like some type of removable storage device.

---

### Post by z987k on 2007-02-15
Well I finally figured it out, I don't understand why this is and would like to fix it, but to get the a710 to work with gthumb, you need to be root.  I just ran "sudo gnome-volume-manager-gthumb" and no errors, imported the photos to a folder and everything is great.  
I would like to make it so I can do this as a regular user though.

Zach

---

### Post by DarthTibault on 2007-03-16
In case you haven't found the solution, or for the other people with this problem, here is the fix:
```
sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
```

Now edit line 3 from
```
BUS!="usb*", GOTO="libgphoto2_rules_end"
```
to this:
```
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
```

Then restart udev
```
sudo /etc/init.d/udev restart
```
and you're done!
I have the same camera, so I guarantee this works ;)

---

### Post by z987k on 2007-03-27
Sweet thanks!  They should patch this or something.

On another and completely random note, when I restarted udev my music got way louder, oh well.

---

