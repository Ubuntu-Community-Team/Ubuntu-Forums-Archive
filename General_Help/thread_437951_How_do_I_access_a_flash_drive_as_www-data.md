---
title: "How do I access a flash drive as www-data?"
date: 2007-05-09
forum: General Help
---

### Post by nathanziarek on 2007-05-09
I'm writing a PHP script that I want to run from a web page for the GUI (it was supposed to be quick and simple, but isn't turning out that way).

Anyway, all I am looking to do is have a user insert a flash drive, and have this web page look at the contents. Unfortunately, the permissions won't allow www-data to read it.

```
drwx------ 3 username root 16384 1969-12-31 18:00 Z256
```

Is there a way — possibly by editing .hal-mtab — to allow www-data to read **any** flash drive / memory card inserted into the machine?

Thanks,

Nate

---

### Post by nathanziarek on 2007-05-09
Well, here is what I did, in case it helps anyone else out:

in /etc/fstab, I added the lines:

```
/dev/sdb1       /media/card     vfat    rw,user,noauto  0       0
/dev/sdc1       /media/flash    auto    rw,user,noauto  0       0
```

That seems to give www-data enough rights to read the drives, although he can not modify it.

Nate

---

