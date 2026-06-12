---
title: "Remount partition"
date: 2007-04-29
forum: General Help
---

### Post by javalang on 2007-04-29
Hi everyone, i've reinstalled my ubuntu and the previous partition files directory was /media/files but now it is on just /files. How could i remount that to old directory? I just found how to mount windows partition on boot.

Thanks.

---

### Post by raul_ on 2007-04-29
```

sudo nano /etc/fstab

```

and change  /files to /media/files

---

### Post by javalang on 2007-04-29
Ohh, so easy! Thank you very much!

---

### Post by diskotek on 2008-02-13
should we reboot after editing fstab?

---

### Post by apetresc on 2008-02-13
> **diskotek said:**
> should we reboot after editing fstab?

Not necessary, just do ```
sudo umount -a
sudo mount -a
```

---

### Post by az on 2008-02-13
> **diskotek said:**
> should we reboot after editing fstab?

No, just unmount it if it is mounted and then mount it again.

---

