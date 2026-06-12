---
title: "installing .sh"
date: 2007-12-24
forum: General Help
---

### Post by ziploc67 on 2007-12-24
i have a file with the file name ".sh"


how do i install/compile it onto my system?

---

### Post by p_quarles on 2007-12-24
> **ziploc67 said:**
> i have a file with the file name ".sh"


how do i install/compile it onto my system?
My guess is that you don't. Files ending in .sh are usually interpreted scripts, and can be run without installing anything. Anyway, go into the directory where the file is located, and run this:
```
chmod 744 *filename*.sh
```
That will make it executable. Now, run the script:
```
./*filename*.sh
```

---

### Post by Sef on 2007-12-25
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

