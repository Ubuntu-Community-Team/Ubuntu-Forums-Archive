---
title: "resize root partition"
date: 2017-01-03
forum: General Help
---

### Post by aliahmadi1367 on 2017-01-03
Hi,
I have install ubuntu 16.10 beside of windows 10 on a ssd.
I want to increase the size of root partition
how can i do that without loosing the data also the grub bootloader?
thanks

---

### Post by alexandari on 2017-01-03
Hi,

You can use a tool called Gparted. There is also a LiveCD/LiveUSB version. You may want to use that one, in order to increase the size of the root partition. It's got a GUI and it's quite easy.

Cheers

---

### Post by aliahmadi1367 on 2017-01-03
thanks
but my concern is loosing grub boot loader

---

### Post by Keith_Helms on 2017-01-03
Resizing the partition will not hurt the grub boot loader.  Just don't do anything like format the drive.  You will need unused space directly following the root partition.   Boot from a live disc/usb drive and then run gparted.  Select the partition, then from the partition menu select resize/move.

---

### Post by aliahmadi1367 on 2017-01-03
resizing procedure is as follow:
shrinking the windows 10 volume and get 50GB free space the move the unallocated space near the ubuntu ext4 .
then merge the free space with ext4.
is this ok?

---

### Post by Keith_Helms on 2017-01-03
> **aliahmadi1367 said:**
> resizing procedure is as follow:
shrinking the windows 10 volume and get 50GB free space the move the unallocated space near the ubuntu ext4 .
then merge the free space with ext4.
is this ok?

Assuming you meant Windows 10 **partition** and not volume, yes.  If the Ubuntu partition is directly followed by the Windows partitions, you would need to
1. Shrink the windows partition.
2. Move the windows partition up to the end of the free space so that the free space then is directly after the Ubuntu partition.
3. Increase the size of the Ubuntu partition.

---

