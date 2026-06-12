---
title: "Permanent Mount Bind?"
date: 2007-07-16
forum: General Help
---

### Post by hooksie on 2007-07-16
OK, I've learned that you can have a permanent mount point for s disk by editing /etc/fstab.

However, what I would like to do is have a permanent mount --bind.  Anyway I can do this?

---

### Post by kidders on 2007-07-17
Hi there,

Sounds like you want to rebind all/part of a filesystem to a mount point ... as you might do with /dev, for example, before chrooting into another environment. If so, you can simply add a line to /etc/fstab, as you mentioned. Pretty much anything you can do with a "mount" command can be done with /etc/fstab. :-)

---

### Post by DaVinciXL on 2008-02-18
Of course, this answer might come a "little" too late for you - but maybe just in time for others.

You can simply creat new "mountpoints" in /etc/fstab which have to look like this

```

/data           /nfs4exports/data   none    rw,bind 0   0
/home           /nfs4exports/home   none    rw,bind 0   0

``` 

In the first column you find the original directory, the next column shows the directory where it should be bound to.

---

