---
title: "gparted dependency problems"
date: 2006-08-05
forum: General Help
---

### Post by stulesnett on 2006-08-05
I have downloaded gparted_0,02.5-1.1_i386.deb and have not been able to install the package Ubuntu 5.10.

I continue get dependency alerts on 3 different libraries and it appears that ubuntu current lib's old than the new gparted.

I've now down loaded an older  version gparted_0.0.8+cvs2005022001-0ubuntu1_i386.deb which seem to archived.  

I don't seem able to expand(?) the file to install it, can someone assist me.

Thanks, Stu](*,)

---

### Post by Jagot on 2006-08-05
It's in the repositories.  You do not need to download the package like that.  From Terminal:

```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by stulesnett on 2006-08-06
Thanks for information.  I followed your instructions and it appears to have worked.

Stu

---

