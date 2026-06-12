---
title: "Compression Ratio"
date: 2008-06-14
forum: General Help
---

### Post by Cephaus on 2008-06-14
Is there a way to increase it on File Roller?

---

### Post by cariboo on 2008-06-14
If you check **man file-roller** in a terminal it dosen't look like it.

If I remember correctly bzip2 does a better job on compressing files, again check **man bzip2**

Jim

---

### Post by Simon-v on 2008-07-04
One way is to open **gconf-editor**, navigate to ***/apps/file-roller/general*** and set ***compression_level*** to "*maximum*", changing the default behavior.

---

