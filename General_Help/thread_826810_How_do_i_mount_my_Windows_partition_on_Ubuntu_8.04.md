---
title: "How do i mount my Windows partition on Ubuntu 8.04?"
date: 2008-06-12
forum: General Help
---

### Post by pk_chester on 2008-06-12
Please Help! and guys can u also tell me a torrent client which has got scheduler ;)

---

### Post by skymera on 2008-06-12
Mount windows, easy =D

```
 sudo mkdir /media/windows
sudo fdisk -l 
```
Choose your drive, sda1 sdb1 etc

[/code] sudo mount /dev/DEVICE /media/windows [/code]

If you want it to auto mount you need to edit your /etc/fstab

---

