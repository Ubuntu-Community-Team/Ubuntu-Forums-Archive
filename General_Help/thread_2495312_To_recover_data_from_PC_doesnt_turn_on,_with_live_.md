---
title: "To recover data from PC doesnt turn on, with live usb"
date: 2024-02-14
forum: General Help
---

### Post by yunusilk on 2024-02-14
Hello. My Ubuntu 22-04 PC stucked at the begining screen. l want to back up my private files from PC to external hard disk. lf l use a live USB, can l see and transfer my files from PC to hard disk?

---

### Post by Frogs Hair on 2024-02-14
Support request, moved to General Help.

---

### Post by SeijiSensei on 2024-02-14
Yes, though you'll have to mount the devices manually. Plug in the USB device, then boot from the installation medium and choose "Try Ubuntu." You can use 
```
sudo fdisk -l
```
to list all the storage devices and any partitions. Find the partition with the data you want to save, let's call it /dev/sda1 for an example, then mount that partition into the fiie system with
```
sudo mount /dev/sda1 /mnt
```
Now use the same process to find the identifier for the partition on the USB drive to which you want to copy data. Mount it to the empty "/opt" directory with
```
sudo mount /dev/sdb1 /opt
```
Now you can copy files from /mnt to /opt. The default "ubuntu" user has root privileges so you shouldn't run into any rights problems.

---

### Post by yunusilk on 2024-02-14
Thank you very much.

---

