---
title: "cant unmount or eject disk"
date: 2005-08-06
forum: General Help
---

### Post by Digitallysick on 2005-08-06
unmount gives error /mnt/cdrom0" busy eject gives /dev/hdc failed, any ideas

---

### Post by jasmuz on 2005-08-06
Most probably you have a program still using the cdrom drive
type sudo eject, for a quick and dirty eject.

---

### Post by Digitallysick on 2005-08-06
that wouldn't even work, it would say "device busy" i had to reboot, sucks

---

### Post by Sam on 2005-08-06
To force unmount:
```
$ sudo umount -f <device>
```

---

### Post by Ufo on 2005-08-06
You could also use "fuser" command in terminal to check what program is still using cdrom device and to kill it's process.

---

