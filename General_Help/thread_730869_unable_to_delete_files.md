---
title: "unable to delete files"
date: 2008-03-21
forum: General Help
---

### Post by Bheegerji on 2008-03-21
My pen drive was infected with some virus through a Windows system. So, I decided to delete all the contents of my pen drive through my Ubuntu. But, when I try to delete these files i get an error message stating that the files cannot be deleted because it's is on a read-only disk. I checked the file permissions and the user was allowed to create and delete files. But I'm not able to delete the contents in my pen drive.

Any suggestions?

---

### Post by Zill on 2008-03-21
Bheegerji:  Suggest reformat your pen drive.  This should remove **all** data.
eg.  Assuming pen drive is sda1...
```
 sudo mkfs -t vfat -v /dev/sda1
```

---

