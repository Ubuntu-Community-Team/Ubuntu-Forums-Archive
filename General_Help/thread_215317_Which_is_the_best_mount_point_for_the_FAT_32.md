---
title: "Which is the best mount point for the FAT 32?"
date: 2006-07-13
forum: General Help
---

### Post by milagre23 on 2006-07-13
Which is the best mount point for the FAT 32 common partition between UBUNTU and xp?

Thanks for your attention

---

### Post by aysiu on 2006-07-13
Wherever you want, actually.

I would put mine at /windows
Some would put theirs in /media/fat32 or /media/storage
Others might put it in /home/milagre/music

Whatever works for you.

---

### Post by milagre23 on 2006-07-13
Thanks for your help. 
I think I've done some mistake and don't know how to handle it. I have a FAT32 partition in the "computer" of the gnome-panel menu but I can't open it. A message appears telling me that in unmounted, I try to mount it but can't

---

### Post by kb2wdi on 2006-07-13
Make partitions automatically available section;

[https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html)

Use vfat as fs type.

---

