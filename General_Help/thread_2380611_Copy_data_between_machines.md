---
title: "Copy data between machines"
date: 2017-12-19
forum: General Help
---

### Post by sed_faster on 2017-12-19
Hello folks,

I simply need copy amount big data between pc Linux (Lubuntu to Ubuntu Server). Should I use rsync? How?
Thanks

[UPDATE1]
Both machines are in same network

---

### Post by QIII on 2017-12-19
Moved to General Help.

---

### Post by aromo2 on 2017-12-19
scp -rp /source/local/dir remoteuser@remotemachine:/destination/dir

-or-

scp -rp remoteuser@remotemachine:/source/remote/dir /destination/local/dir

man scp  ; <== for more options

---

