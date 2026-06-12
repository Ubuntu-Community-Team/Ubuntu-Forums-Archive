---
title: "How does Ubuntu automount?"
date: 2006-09-11
forum: General Help
---

### Post by BenoL on 2006-09-11
Hi there!

I've been wandering how does Ubuntu handle the auto-mounting stuff? I would like to better understand how my system works and maybe try to implement something similar in my gentoo...

It's the hal/dbus I supppose, but what else? I found no ivman/autofs/submount or anything like that on the system. Is it GNOME or KDE specific? gnome-volume-manager for example?

---

### Post by Ramses de Norre on 2006-09-11
Gnome-volume-manager does handle automounting, yes. I use this in fluxbox to automount usb devices and stuff.

---

### Post by BenoL on 2006-09-12
How about Kubuntu? Do they rely on KDE completely?

---

### Post by Thyamine on 2006-09-12
Kubuntu has KDE installed by default, so I'd say it more or less relies on it.  

To mount a partition automatically you can edit your /etc/fstab file.  Basically you create a folder somewhere that you want to mount the partition into.  For example, '/mnt/hdd' or '/mnt/windows'.  

Then in your /etc/fstab file you can add a line for that partition.  There are already a few entries in there, but you basically add in a line for what you want to mount:

(dev)       (mount point)  (type) (options)  (dump) (pass)
/dev/hda1   /mnt/windows   ntfs   defaults   0      0

There are a lot of options, so take a look at something like this: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I bought the Ubuntu Hacks book, and it tells you how in there as well.  I think in the end I used linux-ntfs to for the mount-type ([http://www.linux-ntfs.org/)](http://www.linux-ntfs.org/)), but I'm not on the box so I can't say for sure.

---

### Post by az on 2006-09-12
Before Dapper, kubuntu used ivman for automounting, because KDE was slow to adopt Hal/Dbus.

In Dapper, Gnome and Kde both use Hal and Dbus.

---

