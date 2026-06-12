---
title: "File permission puzzle..."
date: 2006-07-11
forum: General Help
---

### Post by TeeAhr1 on 2006-07-11
Deleted

---

### Post by digby on 2006-07-11
what is the output of```
ls -l /usr/local/lib/last-exit
``` In anycase, you should be able to remove it w/ ```
sudo rm filename
``` If that -for some reason- doesn't work, maybe try chown to make someone the owner of the file?

---

