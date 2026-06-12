---
title: "Folders are locked"
date: 2006-11-15
forum: General Help
---

### Post by chris23 on 2006-11-15
Some folders in my hard disk (fat32) are locked and i don't have access to them. Some others are unlocked on the same partition...what is wrong?
How can i unlock them??

---

### Post by aysiu on 2006-11-15
Moved to a more appropriate forum.

---

### Post by earobinson on 2006-11-15
are you sure they are on the same partition. eg is there a folder that contains both folders you can and cant write to?

if so can you give us the ls -l output from that folder and tell us what folders you can and can not write to?

Thanks.

---

### Post by Ramses de Norre on 2006-11-15
How is the fat partition mounted?
Could you show the output of following command?
```
cat /etc/fstab
```

---

### Post by chris23 on 2006-11-16
ok i solved the problem with chmod 777

---

