---
title: "Quick Question"
date: 2007-07-28
forum: General Help
---

### Post by jukari on 2007-07-28
I want access to write to my NTFS HDs while in linux... I have access to see and read the files but it will not let me write files to it unless im under root... 

Since I don't know how to run a window under "root" like the "Run As" command in windows... how can I get full access to my hard drives with a few simple clicks or so?

Thank you.

---

### Post by logos34 on 2007-07-28
you can't write to windows natively from linux, even as root...you need a special driver:

sudo apt-get install ntfs-3g ntfs-config

Once it's installed go to apps>sys tools>ntfs config 

enable write support to internal and/or external devices and create a mount point. like 'windows', etc...it will mount it under /media directory.  Reboot if necessary.

---

### Post by jukari on 2007-07-28
Thank you very much!

---

