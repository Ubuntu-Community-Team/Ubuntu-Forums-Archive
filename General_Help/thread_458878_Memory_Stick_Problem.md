---
title: "Memory Stick Problem"
date: 2007-05-30
forum: General Help
---

### Post by godmode117 on 2007-05-30
hi, im having memory stick problems. when i insert a memory stick everything goes fine, the disk shows up on the desktop and the file browser opens so i can read/write files. so i try and copy a file and it works, but when i remove the drive its as if nothing copied and the drives blank.  please help this is very frustrating.

---

### Post by public_void on 2007-05-30
Right click on the desktop icon and select eject. This unmounts the device and writes the files. The reason is linux buffers the data to write later, ejecting the device forces the data to be written.

---

