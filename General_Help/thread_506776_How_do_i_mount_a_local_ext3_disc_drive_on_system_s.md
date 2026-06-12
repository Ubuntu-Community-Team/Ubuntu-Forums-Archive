---
title: "How do i mount a local ext3 disc drive on system startup?"
date: 2007-07-22
forum: General Help
---

### Post by Ryukenden on 2007-07-22
I have Ubuntu installed on a primary IDE slave disc drive but my primary IDE master disc drive doesn't automatically mount on system startup.
 How do i configure Ubuntu so that the primary IDE master mounts automatically on startup for all or at least my user? The drive is formatted as ext3.

Greetings, Gabriel

---

### Post by Stephen Howard on 2007-07-22
Add a line to your /etc/fstab file.  Something like:

```
/dev/sdaXX   /my/mount/point      ext3    defaults                        0       2
```

---

### Post by 5-HT on 2007-07-22
You can add it to your/etc/ fstab using the options that are described in that file for your slave disk (just replace the device and the mountpoint).
Please refer to the manual pages for 'mount' and 'fstab' for more information. 
cheers,

---

### Post by Ryukenden on 2007-07-23
Thank you very much. It worked!
But now how do i remove the disk icon from my desktop and locations menu (i'm not sure if this is the menu's correct name since i'm using a Portuguese version of Ubuntu)?

---

### Post by distroman on 2007-07-23
Think this should take care of the desktop icon.
```
gconftool-2 --type bool /apps/nautilus/desktop/volumes_visible --set false
```

---

### Post by Ryukenden on 2007-07-26
It worked. Thanks

---

