---
title: "E2fsck exit code 1"
date: 2020-12-14
forum: General Help
---

### Post by Macamba on 2020-12-14
It is a bit confusing when you run an repair on a partition that needs fixing and you get the following Error message ([https://ibb.co/4pZ7ghy](https://ibb.co/4pZ7ghy)):
```
Error while repairing filesystem
Error repairing filesystem on /dev/sda3: Process reported exit code
1: e2fsck 1.44.1 (24-mar-2018)
(udisks-error-quark, 0)
```

Searching the Internet I found out it stands for "1    - File system errors corrected". So everything is alright? 

(Sorry, I pressed the Submit button before my post was finished :mad:)

---

### Post by ActionParsnip on 2020-12-14
Did you perform the check on the file system when it was unmounted?

---

### Post by Macamba on 2020-12-14
Probably not. Will check when I boot Linux again.

---

### Post by Macamba on 2020-12-15
> **ActionParsnip said:**
> Did you perform the check on the file system when it was unmounted?

No. But when I performed the check on the unmounted system it ended without an error message. Thanks.

---

