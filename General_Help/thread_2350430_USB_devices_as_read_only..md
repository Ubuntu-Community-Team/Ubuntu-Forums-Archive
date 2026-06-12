---
title: "USB devices as read only."
date: 2017-01-24
forum: General Help
---

### Post by calvta on 2017-01-24
Is it possible to have 16.04.1 desktop make all USB devices as ready only. I would like to create a desktop where people can view data on USB drives but not alter or delete the data. I would also like and prevent them from changing the desktop settings. Is something like this even possible.?

Thank You

---

### Post by TheFu on 2017-01-25
"all usb devices"?  Probably not, but maybe. I'm under the impression that most new systems come with USB mice and USB keyboards.  If you want the mouse to work and the keyboard to work, then those devices must be read-write.

There are 2 basic things in Linux - files and processes.  Everything is either a file or a process.  All files have permissions that can be manipulated. You can make them read-only for selected userids.  Different programs may handle that poorly, but you can do it.  If you like, you can make it so that a $HOME is not modifiable by the userid it belongs to. GUI programs might not like this and may crash if they don't handle that well (not being able to save their settings). Some non-GUI programs might have issues too, but generally, I've seen GUI programs like web browsers have the most issues in the past.  A base knowledge about file and directory permissions will let you play around with this. There are lots of tutors for that online.  BTW, directories are just "files" to Linux. ;)

As for USB storage as read-only, I would do that over a network connection. Then you wouldn't have to worry about the storage walking off and read-only storage is easy.

Have you looked into the "Guest" account on Ubuntu? It gets created whenever someone logs in using it following a template and it is removed when they logout. It has a random name and limited permissions on the system.

---

### Post by sudodus on 2017-01-25
> **calvta said:**
> Is it possible to have 16.04.1 desktop make all USB devices as ready only. I would like to create a desktop where people can view data on USB drives but not alter or delete the data. I would also like and prevent them from changing the desktop settings. Is something like this even possible.?

Thank You

Do you want some particular USB drives to be read-only? It is possible to create them with a read-only file system, for example ISO9660. Or do you want all USB drives read-only on this particular computer? Then you should modify how they are mounted, and then restrict the user to the guest session as suggested by TheFu.

---

