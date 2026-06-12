---
title: "Cannot resize windows partition"
date: 2007-10-05
forum: General Help
---

### Post by FRuMMaGe on 2007-10-05
I've been trying to install Ubuntu on my brothers PC.  I have defragged the windows partition several times and have tried numerous programs (including gparted on the disk) but the partition will not resize!

All it says is "error resizing partition".

What could be wrong?

---

### Post by vanadium on 2007-10-05
I am not sure, but gparted might refuse to resize a partition in an area where data is allocated. That can be the case, even after defragging, if a "non movable" file is located near the end of the partition. Such a file indeed could be your Windows Swap file, and then you could solve the issue by temporarily disabling the Windows swap file. It could be some other "system" file, or a read-only file from another application, though.

---

### Post by FRuMMaGe on 2007-10-09
Sorted!

---

### Post by strabes on 2007-10-09
Please mark the thread as solved.

---

