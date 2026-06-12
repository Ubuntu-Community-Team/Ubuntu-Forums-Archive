---
title: "Master Boot Record"
date: 2006-07-11
forum: General Help
---

### Post by metallcoholix on 2006-07-11
Does anyone knows how to delete of format the /mbr??

---

### Post by diepruis on 2006-07-11
Why do you want to do this?

---

### Post by zigzed on 2006-07-12
> **metallcoholix said:**
> Does anyone knows how to delete of format the /mbr??

you can do this, which will clear the boot code, and keep the partition table.
```
dd if=/dev/zero of=/dev/HDx bs=446 count=1
```

where HDx is your hard disk device.

for safe, you should backup your important data first.

---

### Post by jackson0905 on 2006-07-12
Go to the dos.
type :fdisk /mbr.
then ,just ok

---

