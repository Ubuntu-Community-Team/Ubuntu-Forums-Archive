---
title: "Lifedrive syncing folders"
date: 2006-12-22
forum: General Help
---

### Post by peter_brewer on 2006-12-22
I'm not sure where to put this question since I can't find a category which fits it well.

I use a Palm  Lifedrive PDA and am wondering if it is possible to set up rsync or something similar to synchronise folders on the device with folders on my desktop over usb.  It is basically like a flash disk when connected to the computer.

Any help you can offer would be greatly appreciated.  I've tried reading documentation but it is confusing me.

---

### Post by gangalee on 2007-11-12
put the Lifedrive in drive mode

mount it, probably with something like 
```
sudo mkir /mnt/lifedrive 
sudo mount /dev/sda /mnt/lifedrive
```

then rsync whatever /mnt/lifedrive/

---

### Post by photoboot on 2008-03-21
Hi there,

you can put the Lifedrive in drive mode, connect it to the usb, and then type in terminal:

```
$blkid
```

Then, lookt at the /dev/sdxx where the lifedrive is, and finally 
```
$sudo mkdir /media/lifedrive
$sudo mount -t vfat /dev/sdxx /media/lifedrive
```

thats it:)

---

