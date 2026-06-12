---
title: "recover rm -r folder"
date: 2007-06-08
forum: General Help
---

### Post by blmartin777 on 2007-06-08
I am just doing some testing and wanted to know if you rm -r a folder can you recover it. I did a default feisty install so I have ext3. I have read that you can't with ext3 but I am just checking.

Thanks

---

### Post by 505 on 2007-06-08
No you can't. Delete it with rm and it's gone. Ext3 blanks all deleted files with 0's, so there is no recovering.

---

### Post by init1 on 2007-06-08
> **505 said:**
> No you can't. Delete it with rm and it's gone. Ext3 blanks all deleted files with 0's, so there is no recovering.
505 is right. There are undelete programs available, but they work on ext2, not ext3.

---

