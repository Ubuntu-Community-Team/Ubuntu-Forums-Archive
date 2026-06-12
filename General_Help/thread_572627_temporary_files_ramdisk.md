---
title: "temporary files ramdisk"
date: 2007-10-10
forum: General Help
---

### Post by markp1989 on 2007-10-10
i have already created a 200mb ram disk, mounted at /mnt/rd 

i was wondering if it is possible to set it up so that all temporary files get stored in this ram disk. 

i have 2gb of ram, and i have never seen more then 1.1 gb in use

im nt sure if i just mount the ramdisk in /tmp (im not sure if this will cause problems) or if i have to do other settings

---

### Post by milosz.galazka on 2007-10-10
You could mount ramdisk to */tmp* (and create link from */var/tmp* to it).
The good solution will be to do this at system startup (like putting commands in */etc/rc.local*).

But the better solution will be (probably) to just leave that memory so system will use this memory as cache for hard disk operations.

---

### Post by markp1989 on 2007-10-12
> **milosz.galazka said:**
> You could mount ramdisk to */tmp* (and create link from */var/tmp* to it).
The good solution will be to do this at system startup (like putting commands in */etc/rc.local*).

But the better solution will be (probably) to just leave that memory so system will use this memory as cache for hard disk operations.

thanks for a quick reply, i have shrunk the ram disk to 50mb and i currently run swiftfox from it

---

