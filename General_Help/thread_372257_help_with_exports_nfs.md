---
title: "help with exports nfs"
date: 2007-02-28
forum: General Help
---

### Post by nephish on 2007-02-28
lo there all,

i have a home network with one ubuntu box acting as the gateway / router for the other two computers in the house. 
i want to share a folder called /mnt/stuff

i can already get it mounted on my wifes ubuntu box with 
mount 1992.168.1.1:/mnt/stuff /stuff

i have a line in my /etc/exports like this
/mnt/stuff 192.168.1.2(rw,sync)  but i want all the computers on my lan to be able to mount it.
can i do that with just one line ?

---

### Post by kidders on 2007-02-28
Hi there,

You can indeed.

```
/mnt/stuff 192.168.1.0/24(rw,sync)
```... depending on what your own netmask is.

There *are* other ways of doing this, but this one would open the share to anyone on your subnet.

---

### Post by nephish on 2007-02-28
thanks man , worked like a charm.

---

