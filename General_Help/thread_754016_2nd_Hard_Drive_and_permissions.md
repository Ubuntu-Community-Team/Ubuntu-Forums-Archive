---
title: "2nd Hard Drive and permissions"
date: 2008-04-13
forum: General Help
---

### Post by estanton on 2008-04-13
So the toher day I've suddenly had problems with the read-write permissions on my second hard drive. When I mount the drive it lets me write to the drive but fairly quickly it locks up and becomes read only. This is a real pain and when I try and set the permissions via the properties for the drive it won't let me change thems tating I don't have permission. Any advice on how to fix this problem? Thanks!

---

### Post by sekinto on 2008-04-13
In the properties dialog does it say you have permission to read/write?
If it doesn't you can change the permissions in that dialog if you use "gksudo nautilus".

---

### Post by RTrev on 2008-04-13
> **estanton said:**
> So the toher day I've suddenly had problems with the read-write permissions on my second hard drive. When I mount the drive it lets me write to the drive but fairly quickly it locks up and becomes read only. This is a real pain and when I try and set the permissions via the properties for the drive it won't let me change thems tating I don't have permission. Any advice on how to fix this problem? Thanks!

If it lets you write to it initially, but then changes, could it be that the drive has hardware problems?  If you have a copy of Steve Gibson's SpinRite lying around, that's what I'd try on this drive.

If it were a permission problem, it should remain constant.. not change in mid-stream, no?

HTH,
Bob

---

### Post by estanton on 2008-04-13
yeah the variation does seem weird, it's not acting up at the moment. I'm leaning towards Transmission doing something weird.

---

### Post by estanton on 2008-04-21
Well it stopped for a few days and now the HD is locking out again. When I go and look at it's properties it states the owner is root and I can't even unmount the the drive.

---

### Post by bodhi.zazen on 2008-04-21
I agree, sounds like a hard ware problem, the drive may be just short of total failure. I suggest you start with a backup of the data on the device.

---

