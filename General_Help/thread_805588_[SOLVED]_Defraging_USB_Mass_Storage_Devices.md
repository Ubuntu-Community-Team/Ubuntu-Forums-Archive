---
title: "[SOLVED] Defraging USB Mass Storage Devices"
date: 2008-05-24
forum: General Help
---

### Post by guitarMan666 on 2008-05-24
I have two USB Mass Storage Devices that are in DESPERATE need of defragmentation.  Is there a Linux utility that will do that for me, I don't feel too comfortable using a written-for-Windows defragmenter through Wine unless I absolutely must.

---

### Post by cdtech on 2008-05-24
Are these Linux OS disk?

---

### Post by geo909 on 2008-05-24
If they are ext2 or ext3, you probably won't ever need to defragment them.

If they are NTFS I would **strongly** recommend to boot to windows (it's not a sin ;) ) or go to a friend of yours who has windows on his machine (I'm sure you have plenty of them!) and defragment it there.
I think I have heard of a NTFS defrag tool for linux but I assume you will risk a lot by using it.

Also, I'm not sure if you can use defragment tools through wine.

If you talk about FAT I don't really know.

---

### Post by fsmithred on 2008-05-24
If you have enough hard drive space, copy the files from the USB storage to hard drive, delete files from USB storage, then copy them back from the hard drive.

---

### Post by prshah on 2008-05-24
> **guitarMan666 said:**
> I have two USB Mass Storage Devices that are in DESPERATE need of defragmentation.  Is there a Linux utility that will do that for me, I don't feel too comfortable using a written-for-Windows defragmenter through Wine unless I absolutely must.

Defragging is useful only on HDD's. If you have flash drives, they don;t need to be defragged. Defragging helps reduce access time by reducing seeks by the drive heads. Flash drives are SSD (solid state devices) which have no seek time as such.

---

### Post by guitarMan666 on 2008-05-25
Actually they are flash devices so i guess they don't need it.
Thanks

---

