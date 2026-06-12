---
title: "How do I find out information about my hard disk?"
date: 2007-01-21
forum: General Help
---

### Post by Coop on 2007-01-21
Hello
How do I find out information about my hard disk,like partitions,total size and free space?
The computer thing in the Places menu doesn't tell much.
Please answer me.
I will be highly obliged for your help.
Ahmed

---

### Post by taurus on 2007-01-21
Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by dexter on 2007-01-21
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

Or System->Administration->Disks

---

