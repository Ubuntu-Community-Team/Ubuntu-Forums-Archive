---
title: "Copy/ Make Directory (in /proc)"
date: 2008-05-29
forum: General Help
---

### Post by WRDN on 2008-05-29
Hi,

Somehow ive managed to delete the "asound" folder in the /proc folder.
Now, i have lost all sound.

Ive booted from the Live CD, and have made a copy of the asound folder.

Is it possible to copy the "asound" folder to the /proc folder?

Ive tried making a directory in the /proc folder to put the files in, but the result is 

> mkdir: cannot create directory `test': No such file or directory

Ive also tried using the "cp" commands to copy the folder, but to no avail.

**How can I copy the asound folder to /proc?**

Thank you.
WRDN


**EDIT**: Does anyone know what package "asound" is contained in, as I could reinstall it from the disk.

---

### Post by Vadi on 2008-05-29
Try reinstalling "libasound2".

---

### Post by bingoUV on 2008-05-29
In general, you are not supposed to create, delete files in /proc. Files in this directory are automatically populated by the kernel. Try rebooting. If your deleting of the directory did not do any permanent damage (hopefully) then the directory you are missing will get created again.

Files on /proc do not occupy space on your hard disk. I don't understand why you deleted the directory.

---

