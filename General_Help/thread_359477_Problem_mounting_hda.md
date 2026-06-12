---
title: "Problem mounting hda"
date: 2007-02-12
forum: General Help
---

### Post by carverj on 2007-02-12
G'day
```
root@ubuntu:/# mount -t ntfs /dev/hda /media/hda
mount: block device /dev/hda is write-protected, mounting read-only
mount: /dev/hda already mounted or /media/hda busy

```
I installed Vista to hda as master and am attempting to mount it viaUbuntu  Live CD with the error above. I then plan to mount hdb2 to copy over a partimage image of a ubuntu partition from DVD to the primary drive. 
Just wondering why I cannot mount Vista though !!??
Cheers 
& have a good one

---

### Post by nereid on 2007-02-12
Because hda is the whole harddisk device. You need to mount a single partition from it, like hda1 or hda2 (depending on your partition layout).

---

