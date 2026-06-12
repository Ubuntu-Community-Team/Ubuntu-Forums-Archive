---
title: "Not auto-mounting USB drives"
date: 2008-05-16
forum: General Help
---

### Post by rrwo on 2008-05-16
I have a new install of Xubuntu Hardy on a new 64-bit machine (ThinkPad R61i).

It's not auto-mounting external drives that are plugged into the USB ports (a flash drive and a phone).  They work on another machine running Hardy.

I've got auto-mounting enabled according to the settings, and I've checked that my user has privileges according to the Users and Groups applet.

The devices come up when I use "lsusb" for one of the ports, but not the other two (lsusb seems to crash).  I don't know if this is related, though plugging the devices in the port that lsusb works for still doesn't work.

Any help would be appreciated.

---

### Post by heatblazer on 2008-05-16
Have you tried to mount them manually? See <man mount> in console

---

### Post by rrwo on 2008-05-16
Yes. It's not working either: it's saying that the devices /sb[bcd]1 do not exist!

---

### Post by rrwo on 2008-05-17
For whatever reason, the problem went away after rebooting.

---

### Post by rrwo on 2008-05-19
Never mind. It's come back. (I've also noticed another thread by sometone with the same problem.)

I'm wondering if it's connected to the sound problems Ubuntu used to have where the sound worked fine on a fresh (re)boot but not when resuming.

---

