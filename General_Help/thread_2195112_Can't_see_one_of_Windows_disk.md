---
title: "Can't see one of Windows disk?"
date: 2013-12-22
forum: General Help
---

### Post by zrzhu11 on 2013-12-22
I installed Ubuntu 12.04 within windows 8 in E: drive. Now I can see C and D drive in Ubuntu, but I can't see E drive. Because I installed ubuntu on E drive? Thanks.

---

### Post by Impavidus on 2013-12-22
Those drive letters are meaningless in Ubuntu.

Did you install using wubi? It is known to not work very well with Win8, but maybe it works in your case. If that's the case, the E partition is not visible because it is not available to be mounted. That is because it is already mounted, at /host. That is where you'll be able to find all files on the E partition.

---

### Post by zrzhu11 on 2013-12-22
> **Impavidus said:**
> Those drive letters are meaningless in Ubuntu.

Did you install using wubi? It is known to not work very well with Win8, but maybe it works in your case. If that's the case, the E partition is not visible because it is not available to be mounted. That is because it is already mounted, at /host. That is where you'll be able to find all files on the E partition.
Yes, I installed it using wubi. Which folder should I check for the file from E partition?

---

### Post by Impavidus on 2013-12-22
/host/

---

### Post by zrzhu11 on 2013-12-22
> **Impavidus said:**
> /host/
Found it. Thanks. :p

---

