---
title: "Copying of files"
date: 2018-09-02
forum: General Help
---

### Post by AnupamMitra on 2018-09-02
My Desktop OS is Ubuntu 18.4.1. While copying MP4 files from my desktop to Memory Card (via ctrl + C or the right-click menu) it freezes and stuck in midway. I adopted this procedure frequently while the desktop environment was Ubuntu 16.04.1. Any advice how to resolve it?

---

### Post by ajgreeny on 2018-09-02
Copying files from where to where, and what size are the files?

Do you have the correct permissions, particularly for the destination folder?

---

### Post by HermanAB on 2018-09-02
There are some horrid bugs in the USB subsystem that surface from time to time depending on the hardware.  You can try using 'ionice' and 'rsync' to make copying robust.

---

### Post by AnupamMitra on 2018-09-02
> **ajgreeny said:**
> Copying files from where to where, and what size are the files?

Do you have the correct permissions, particularly for the destination folder?

I already mentioned that copying from a Folder in my Desktop to Memory Card (Sandisk) kept in a Card Reader. The size of the files (MP4), say 450 MB & 560 MB.

---

### Post by AnupamMitra on 2018-09-02
> **HermanAB said:**
> There are some horrid bugs in the USB subsystem that surface from time to time depending on the hardware.  You can try using 'ionice' and 'rsync' to make copying robust.

Would you please help me to know further details about 'ionice' and 'rsync'? How to use it?

---

### Post by dragonfly41 on 2018-09-02
You might start with installing grsync which comes with a gui and you can do test runs while experimenting.

---

### Post by AnupamMitra on 2018-09-11
Thanks to all for their co-operations. Everything was done as suggested. But there was no result, which is quite unusual. Then I changed the Memory Card and now there is no such trouble for copying of files etc. Sorry for the trouble.

---

