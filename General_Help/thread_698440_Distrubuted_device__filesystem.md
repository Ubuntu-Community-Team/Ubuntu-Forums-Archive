---
title: "Distrubuted device / filesystem"
date: 2008-02-16
forum: General Help
---

### Post by Meson on 2008-02-16
I have a laptop, a desktop, an external hard drive, and 2 flash drives.

Does anyone know of a good way to not only sync these three devices, but track information about which device has what files?  I don't want them to all be the same.  I also want to avoid making one the "server."

I was thinking about something where I'd have a directory for each device and use hard links and/or symbolic links to make sure they are all in sync.

So every device would have a list of all the files that were on all of the other devices using hard links (so as not to waste space)  and possibly broken symbolic links to keep track of what they do not have.

But then, this might not be the right direction to take.  Does anyone have any experience with managing multiple filesystems like this?

---

### Post by chrisccoulson on 2008-02-16
I'm a bit confused about what you're asking.
> Does anyone know of a good way to not only sync these three devices
and
> I don't want them to all be the same
...appear to conflict each other. If you sync the devices, then they'll be the same.

And I don't think you can have hard links across device boundaries.

Anyway, have you tried rsync? There is also a graphical front end, called grsync. They're both an apt-get away.

---

### Post by Meson on 2008-02-16
I meant sync the files the belong on the devices, but not the ones that don't.  We'll use my music for example.

I want all of my music on the desktop and the external drive, no music on the usb keys, and about 3/4 of it on the laptop.  But I also don't necessarily want to assume there is a device which contains all of the music.

I didn't mean to span links across devices, I meant across the directory structure on the individual devices.

Right now I'm using a serious of scripts that I wrote using rsync, but they're not as universally flexible as I'd like them to be.

---

