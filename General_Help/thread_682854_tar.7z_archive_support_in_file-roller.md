---
title: "tar.7z archive support in file-roller?"
date: 2008-01-30
forum: General Help
---

### Post by miatawnt2b on 2008-01-30
I would like to archive some things using p7zip, but first need to archive using tar. I have downloaded the p7zip-full package for gusty and file-roller now has 7z support, but there is not an option to actually create a tar.7z on the fly.  Is there a way to get this support in fileroller or any other program?

Thanks,
-J

---

### Post by Fixman on 2008-01-30
> **miatawnt2b said:**
> I would like to archive some things using p7zip, but first need to archive using tar. I have downloaded the p7zip-full package for gusty and file-roller now has 7z support, but there is not an option to actually create a tar.7z on the fly.  Is there a way to get this support in fileroller or any other program?

Thanks,
-J


```

tar -cvvf file.tar file && 7z a file.tar.7z file.tar && rm file.tar

```

---

### Post by Fixman on 2008-01-31
Did it work?

---

