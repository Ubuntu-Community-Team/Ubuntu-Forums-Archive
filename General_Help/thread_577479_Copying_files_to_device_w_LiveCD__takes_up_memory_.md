---
title: "Copying files to device w LiveCD  takes up memory space"
date: 2007-10-16
forum: General Help
---

### Post by MarkGilmore on 2007-10-16
When I copy a sizable file to a thumb drive (using Live CD), my free memory space decreases by the approx size of the file. I can verify this by entering the "free" command before and after the copy.
What in the world is going on here ??
Thanks !

---

### Post by picopir8 on 2007-10-16
Sounds like its just cashing the file.

I think USB key is mounted with default mount options which sets up an asynchronous IO interface with the file system.

To fix it edit the /etc/fstab file to make it synchronous. then umount and remount.   However, when you reboot the settings will be lost because the fstab is regenerated every time by the liveCD.

---

