---
title: "df -h doesn't report used space correctly"
date: 2015-05-21
forum: General Help
---

### Post by Dimas on 2015-05-21
We've an Ubuntu Server 14.04 and this is the second time we've an alert about the free space remaining. Df -h says that we have 87% of the space in use (94G of 113G) but that isn't real.

```
276861220       total
225056808       mnt
45309880        var
2406420 usr
2182100 home
1186620 opt
489004  lib
67280   boot...
```

It's impossible that from /var to below occuppies 94G!

Rebooting the server solves that, but it's very annoying beacuse it's a production server.

Any ideas?

---

### Post by sudodus on 2015-05-21
Try with sync, see

```
man df
```

```
      --sync invoke sync before getting usage info
```


```
df -h --sync
```

---

