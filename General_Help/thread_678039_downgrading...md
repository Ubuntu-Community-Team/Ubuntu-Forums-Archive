---
title: "downgrading.."
date: 2008-01-25
forum: General Help
---

### Post by Peter Sommer-Larsen on 2008-01-25
I just ran a ```
sudo aptitude dist-upgrade
```

Now my wireless network dosent work.. how do I see what has been upgraded
so I can down-grade it..!?

---

### Post by cdenley on 2008-01-25
Besides the output of that command, you can try

```

ls -l /var/lib/dpkg/info|grep 2008-01-25

```

---

### Post by IcemanV9 on 2008-01-25
Better yet ...
```
less /var/log/aptitude
```
It will give you a great detail on what have been installed, removed or updated.

---

