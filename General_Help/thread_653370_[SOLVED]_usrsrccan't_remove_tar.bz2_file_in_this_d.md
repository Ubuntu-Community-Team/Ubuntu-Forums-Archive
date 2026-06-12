---
title: "[SOLVED] usr/src:can't remove tar.bz2 file in this directory"
date: 2007-12-29
forum: General Help
---

### Post by ivansf92 on 2007-12-29
I downloaded a file to the directory usr/src with the wget command and now I cannot remove it because I do not have "permissions to change it or its parent folder". Is there any way to remove it?

---

### Post by taurus on 2007-12-29
```
**sudo** rm /usr/src/*filename*
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

