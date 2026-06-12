---
title: "Resizing Encrypted partition"
date: 2014-08-23
forum: General Help
---

### Post by fred-020 on 2014-08-23
I was following the tutorial [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions) to enlarge the size of my encrypted partition, but then I got to the part about using fdisk to delete and then re-create a larger crypt partition, but after I created the bigger partition, the system doesnt recognize the partition as an encrypted one anymore... When I try to run the command

sudo cryptsetup luksOpen /dev/sda5 crypt1

it reads

Device /dev/sda5 is not a valid LUKS device.

I was wondering what I could do to make it realize it's an encrypted one..

---

### Post by fred-020 on 2014-08-28
bump

---

### Post by fred-020 on 2014-08-28
bumpy

---

### Post by fred-020 on 2014-08-30
bump

---

### Post by fred-020 on 2014-08-30
> **fred-020 said:**
> bumpy
:d

---

