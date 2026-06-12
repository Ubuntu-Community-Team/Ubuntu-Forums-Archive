---
title: "viewing tune2fs interval for devices"
date: 2006-12-10
forum: General Help
---

### Post by fugrammer on 2006-12-10
hi, how can i know the interval set for the filesystem or device to be check by e2fsck? e.g. after 'tune2fs /dev/fd0 -c 5000', how can i check the value again in future? thanks.

Thomas.

---

### Post by mitch.c on 2006-12-11
> **fugrammer said:**
> hi, how can i know the interval set for the filesystem or device to be check by e2fsck? e.g. after 'tune2fs /dev/fd0 -c 5000', how can i check the value again in future?
List the superblock (replace /dev/sda5 with your device):
```
$ sudo tune2fs -l /dev/sda5 | grep Check
```

---

