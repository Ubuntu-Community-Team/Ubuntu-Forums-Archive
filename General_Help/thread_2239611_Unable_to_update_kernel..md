---
title: "Unable to update kernel."
date: 2014-08-14
forum: General Help
---

### Post by Garchomps on 2014-08-14
It says my boot partition is too small. 
I used to fix this by removing the old kernels, but now the new ones take up too much space. 
I need to free up about 25 mb but the only kernel installed is the one in use.
I can't resize my boot partition because the entire drive is encrypted. 
How do I update my kernel?
The partition is the default 150 mb btw.

---

### Post by Garchomps on 2014-08-15
bump

---

### Post by claracc on 2014-08-15
Here you have: [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions) a step by step guide in order to resize your encrypted partition.

---

### Post by claracc on 2014-08-15
Also, you can find this thread useful: [http://ubuntuforums.org/showthread.php?t=2239635](http://ubuntuforums.org/showthread.php?t=2239635)

---

### Post by Garchomps on 2014-08-15
Wouldn't I have to unmount the partition to resize it? How would I manage that from within the OS I've booted into using it? Would there be any complications?

---

### Post by sotiris2 on 2014-08-15
Read the guide claracc posted. You will need a live cd (aka ubuntu install cd/usb). But do not just open gparted and have a go at the partitions. Check the guide since you may have encrypted partitions.

---

### Post by claracc on 2014-08-15
Have you read the guide provided?, all the questions you ask are answered there.

From the forementioned guide:

"Resizing an encrypted partition must be performed from a live CD and support for encryption and LVM are not included on the live CD.

1. Boot the live (Desktop) CD and install lvm2 and cryptsetup. "

" Resizing an encrypted partition is somewhat complicated. WARNING! Although unlikely (each step is reversible), resizing your encrypted partitions may result in data loss. BACKUP YOUR DATA FIRST"

---

