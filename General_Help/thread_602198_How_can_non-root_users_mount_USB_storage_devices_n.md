---
title: "How can non-root users mount USB storage devices not in fstab?"
date: 2007-11-04
forum: General Help
---

### Post by kprateek88 on 2007-11-04
When I plug in a USB storage device, I get a window asking me what I want to do, which mounts the device in question. In Feisty I could unmount most of the times from Konqueror, but I don't get an unmount option in Konqueror in Gutsy. I need to open Dolphin (which I don't use otherwise) for this. How does this mounting and unmounting work? There's no entry for this in /etc/fstab, and yet I (as a non-root user) can mount and unmount the device. What happens "behind the scenes"? Does it use FUSE? How can I do what Dolphin does from the terminal? If I use mount and umount as an ordinary user, it gives the expected error (you are not root and <blah> is not in fstab). Starting Dolphin just to unmount something is too cumbersome.

---

### Post by bingoUV on 2007-11-04
> **kprateek88 said:**
> When I plug in a USB storage device, I get a window asking me what I want to do, which mounts the device in question. In Feisty I could unmount most of the times from Konqueror, but I don't get an unmount option in Konqueror in Gutsy. I need to open Dolphin (which I don't use otherwise) for this. How does this mounting and unmounting work? There's no entry for this in /etc/fstab, and yet I (as a non-root user) can mount and unmount the device. What happens "behind the scenes"? Does it use FUSE? How can I do what Dolphin does from the terminal? If I use mount and umount as an ordinary user, it gives the expected error (you are not root and <blah> is not in fstab). Starting Dolphin just to unmount something is too cumbersome.

A non root user can unmount a device, if it was mounted with such an option. There are various such options (quoted from man mount)

```

**group**  Allow  an  ordinary  (i.e., non-root) user to mount the file
 system if one of his groups matches the group of the device.  

**user**   Allow an ordinary user to mount the file system.  The name
 of the  mounting  user is  written  to  mtab  so that he can unmount 
the file system again.

**users**  Allow  every  user to mount and unmount the file system.

```

---

### Post by kprateek88 on 2007-11-04
> A non root user can unmount a device, if it was mounted with such an option.
In this case Dolphin (along with whatever pops up the "what do you want to do?" dialog when the USB device is plugged in) (running as a non-root user) can mount as well as unmount the device. How can I do this (mount and unmount) from a terminal? How can a non-root user mount the device in the first place? Or is it some daemon running as root which mounts?

---

### Post by bingoUV on 2007-11-04
> **kprateek88 said:**
> In this case Dolphin (along with whatever pops up the "what do you want to do?" dialog when the USB device is plugged in) (running as a non-root user) can mount as well as unmount the device. How can I do this (mount and unmount) from a terminal? How can a non-root user mount the device in the first place? Or is it some daemon running as root which mounts?

Mounting happens by a root daemon (udevd). For me the drives are always mounted, no questions asked. What are the options dolphin gives you? Can you choose the mount point? I guess not.

Dolphin is able to unmount it without root privileges because udev enables a non-root user to unmount the drive by giving an appropriate option to mount.

---

### Post by kprateek88 on 2007-11-05
> 
What are the options dolphin gives you? Can you choose the mount point? I guess not.

The options include "Open in new window" and "Do nothing". I might have seen a "download photos with digiKam", but I'm not sure. I can't choose the mount point.

---

