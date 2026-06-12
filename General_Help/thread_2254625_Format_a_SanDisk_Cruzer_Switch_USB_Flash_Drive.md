---
title: "Format a SanDisk Cruzer Switch USB Flash Drive"
date: 2014-11-28
forum: General Help
---

### Post by fabian12 on 2014-11-28
Hi could someone tell me how i might format a SanDisk Cruzer USB Flash Drive please.

---

### Post by nerdtron on 2014-11-28
Install Gparted from the software center and use it format your flash drive.

---

### Post by fabian12 on 2014-11-28
Was hoping that someone could tell me how to format the flash drive from the command line. But thanks all the same nerdtron

---

### Post by nerdtron on 2014-11-28
To determine the usb disk:
```
fdisk -l
```

  to see the usb flash drive suppose it may be /deb/sdb1
Be sure to unmount it
  ```
umount /dev/sdb1
```
  
Format it
  ```
mkfs.vfat /dev/sdb1
```

---

### Post by fabian12 on 2014-11-28
Thanks nerdtron

---

