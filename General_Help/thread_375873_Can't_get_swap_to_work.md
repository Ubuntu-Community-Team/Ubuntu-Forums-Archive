---
title: "Can't get swap to work"
date: 2007-03-04
forum: General Help
---

### Post by 16777216 on 2007-03-04
I have found that my swap partition has been added to the fstab file and I am not sure how to add it with the UUID system that Edgy uses

The swap partition is located at /dev/hdb6 and is of type linux-swap with a size of 4.0GB.

---

### Post by Ramses de Norre on 2007-03-04
Add this:
```
/dev/hdb6 none            swap    sw              0       0
```
The old system with specifying device nodes still works perfect.

---

### Post by 16777216 on 2007-03-04
That worked perfectly, thank you very much.

---

