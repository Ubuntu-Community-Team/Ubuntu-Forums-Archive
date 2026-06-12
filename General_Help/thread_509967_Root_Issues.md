---
title: "Root Issues"
date: 2007-07-26
forum: General Help
---

### Post by Imashinu on 2007-07-26
I am trying to mount something
```
mount -t ext2 /dev/sda3 /mnt/tmp

```
and whenever I do, I am told that only root can do it. Now this is the first account that I made with ubuntu and it wont let me sign in as root. So what am I expected to do?

---

### Post by aysiu on 2007-07-26
```
sudo mount -t ext2 /dev/sda3 /mnt/tmp
``` Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

