---
title: "Mounted /var/www into wrong place, files vanished"
date: 2013-09-14
forum: General Help
---

### Post by Guillaume_F. on 2013-09-14
I tried to mount --bind my /var/www/ to a dir into my /home/USER/www folder and I inverted the source and destination... Now I think that my /var/www/ is either pointing to nothing or everything is deleted and im about to cry HALP!!!!

 df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/simfs           524288000 389914816 134373184  75% /
none                   3145728         0   3145728   0% /run/shm
/dev/simfs           524288000 389914816 134373184  75% /var/www
/dev/simfs           524288000 389914816 134373184  75% /var/www
/dev/simfs           524288000 389914816 134373184  75% /home/lithiume3/coding


its on a VPS btw

---

### Post by sisco311 on 2013-09-14
Just umount the destination directory; the files should be still there.

---

### Post by Guillaume_F. on 2013-09-14
I tried to umount 
[COLOR=#000000]
dev/simfs 524288000 389914816 134373184 75% /home/lithiume3/coding 

and it's the same -___-

Also sorry about the title :([/COLOR]

---

### Post by sisco311 on 2013-09-14
How did you mount the directory? Can you post the exact command? Also please post the output of:```
mount
```

---

### Post by Guillaume_F. on 2013-09-14
I unmouted two more time the /var/www that was pointing to / and it fixed it :O thanks for the help

---

### Post by sisco311 on 2013-09-14
You are welcome!

---

