---
title: "wrong characters when mounting cdrom"
date: 2007-01-25
forum: General Help
---

### Post by eldersoares on 2007-01-25
hi
i have a problem when mounting a cdrom. the characters ó á í é and others like these dont appear. instead, appears a ? character. i cant copy the files to the hd... appears "generic error". here is my fstab cdrom line. i live in argentina, spanish language. ive already tried to put the iocharset option in fstab, but it didnt work either... thanks!
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by eldersoares on 2007-01-30
PLZ someone help me! i use ubuntu edgy / dell inspiron 6400

---

### Post by Yuzem on 2007-06-21
Just in case someone gets here looking for help the following worked for me:
sudo gedit /etc/fstab
add utf8 to the cdrom mount point.
For example:
```
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,utf8 0 0
```

---

