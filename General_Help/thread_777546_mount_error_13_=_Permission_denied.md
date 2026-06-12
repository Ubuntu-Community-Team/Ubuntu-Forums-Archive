---
title: "mount error 13 = Permission denied"
date: 2008-05-01
forum: General Help
---

### Post by Questor21 on 2008-05-01
Clean install of 8.04, plus an apt-get of smbfs

```
$ sudo mount -t cifs REMOTESHARE MOUNTPOINT -o uid=$USER,gid=users,workgroup=WORKGROUP,iocharset=utf8,file_mode=0777,dir_mode=0777
[sudo] password for USER: 
Password: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

---

### Post by klcom on 2008-08-08
I have the same problem... you solve it?

:confused:

Thx!

---

### Post by klcom on 2008-08-20
nothing......

---

### Post by 3wtobi on 2008-09-08
the option nounix can help you

---

