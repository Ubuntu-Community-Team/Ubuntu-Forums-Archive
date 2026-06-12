---
title: "XFS Can't get fragmentation state"
date: 2016-05-22
forum: General Help
---

### Post by checoimg on 2016-05-22
I tried this command to check the fragmentation on an XFS dilesystem :
```

sudo xfs_db -c frag -r /dev/sdXX
```

and this is what the program shows

```
xfs_db: error - read only 1024 of 32768 bytes
xfs_db: /dev/sdb1 is invalid (cannot read first 512 bytes)

```

---

