---
title: "Permission denied to execute from vfat partition"
date: 2008-06-06
forum: General Help
---

### Post by Jebdm on 2008-06-06
I installed AMD64 Ubuntu 8.04 a few days ago, and almost everything seems to be working great.  I wanted to have a separate partition for my files which could be easily shared between Windows and Ubuntu, so I created a vfat partition and transfered all my files to it.  I edited my fstab to automatically mount it at /userfiles via this line:

```
/dev/sda4	/userfiles	vfat	utf8,uid=1000,umask=000,user,exec 0 0
```

This works perfectly fine for reading and writing files, but execution fails.  Just for testing purposes, I put together a small program and compiled it (inside userfiles).  This worked perfectly, but I'm not able to actually run the program.

I verified that it wasn't a problem with the program by copying the executable into my home directory, where it ran, but nothing I did to get the executable (or any executable, for that matter) to run off my vfat partition worked.  

I searched online for a solution, but in every case the issue was either a missing "exec" option in fstab or bad permissions.  I also checked that I had full permissions via ls -l:

```
-rwxrwxrwx 1 jeb users 12193 2008-06-06 17:29 test
```

Additionally, sudo doesn't help:

```
jeb@albert:/userfiles/dev$ sudo ./test
sudo: unable to execute ./test: Permission denied
```

Until I can get this figured out, I'm just copy-pasting over to /home/jeb, but this isn't an ideal long-term solution.  Does anyone have any idea what I'm doing wrong?

Thanks in advance-
Jeb

---

### Post by hal8000 on 2008-06-06
Try using defaults. The man page for mount has other useful options too.

/dev/sda4   /userfiles    vfta    utf8,defaults    0   0

Defaults will set the file system to auto mount,rw and exec

---

### Post by Jebdm on 2008-06-06
Defaults worked.  Thanks!

---

### Post by robinc on 2008-06-06
[edit: delete this]

---

