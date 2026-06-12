---
title: "SMB server can't find directory"
date: 2005-10-31
forum: General Help
---

### Post by supermarchino on 2005-10-31
I always get this (from my smb log file)

```
[2005/10/31 14:55:10, 0] smbd/service.c:make_connection_snum(615)
  '/home/marco/shared' does not exist or is not a directory, when connecting to [shared]
```

In spite of the fact that '/home/marco/shared' is correctly set as path in smb.conf file.

Any helps?

[Ubuntu 5.10 upgraded from 5.04. Issue does not exist on my other machine with 5.10 fresh install]

Thank you.

---

### Post by supermarchino on 2005-11-04
[QUOTE=supermarchino]I always get this (from my smb log file)

```
[2005/10/31 14:55:10, 0] smbd/service.c:make_connection_snum(615)
  '/home/marco/shared' does not exist or is not a directory, when connecting to [shared]
```

In spite of the fact that '/home/marco/shared' is correctly set as path in smb.conf file.

Any helps?

[Ubuntu 5.10 upgraded from 5.04. Issue does not exist on my other machine with 5.10 fresh install]

Thank you.[/QUOTE]

upz

---

### Post by minh on 2005-11-04
hi,
i don't know, but you can try 
> 
smbtree
smbtree
it simply give the tree directories in the local network

---

