---
title: "fstab: mounting a volume on startup in home folder"
date: 2007-08-30
forum: General Help
---

### Post by Nathan_M on 2007-08-30
Ok, simple question.

In etc/fstab, this mounts the volume successfully:
```
/dev/sda3    /media/share         vfat  iocharset=utf8,umask=000  0    0
```

But this doesn't:
```
/dev/sda3    /home/nathan/share   vfat  iocharset=utf8,umask=000  0    0
```

There's no error or anything. It just doesn't work when I start up. Something to do with permissions I expect.

---

### Post by notwen on 2007-08-30
Just wondering, have you already created the share folder in your home folder?

---EDIT---

Have you tried mounting this partition manually to see if it works?

> mount /dev/sda3 /home/nathan/share

---

### Post by Nathan_M on 2007-08-30
First I tried it without creating the share folder, then I created the share folder and it still didn't work. Mounting manually to /home/nathan/share works, but everything is read-only. If I mount manually to /media/share, everything is normal (full read-write access).

---

### Post by vanadium on 2007-08-30
This should simply work. Did you check the permissions of both mount points to see whether they are different, which could explain the different behaviour?

---

### Post by Nathan_M on 2007-08-30
Oh, this is a little embarassing. It now does "simply work". I don't know if I did something wrong the first few times around, or if one of the things I meddled with fixed it, but thanks for the help guys.

---

### Post by notwen on 2007-08-30
Hey, it's always nice when it just works, lol.  Glad you were able to get your drive mounted. =]

---

