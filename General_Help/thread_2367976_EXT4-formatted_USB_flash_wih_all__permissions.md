---
title: "EXT4-formatted USB flash wih all  permissions"
date: 2017-08-05
forum: General Help
---

### Post by rybshik on 2017-08-05
I need to create an EXT4-formatted partition on a USB flash drive and  write folders/files. The drive will be used on another Linix machine by  any user, so I need to set the the  least restrictive  permissions, so  every user and every process on every machine should be able to read the  drive.

Will "chmod -R 777 /folder"  do?

Thanks

---

### Post by HermanAB on 2017-08-05
Howdy,

You need to create a directory and set the sticky bit.  Then all new files will inherit the owner and permissions of the directory.

So, use "chmod 1777 directoryname"

---

### Post by rybshik on 2017-08-05
> **HermanAB said:**
> You need to create a directory and set the sticky bit.  Then all new files will inherit the owner and permissions of the directory.

So, use "chmod 1777 directoryname" Thanks.
Now if I need all other users/process on all other machines be able to read/copy, but NOT to delete or modify my data?

---

