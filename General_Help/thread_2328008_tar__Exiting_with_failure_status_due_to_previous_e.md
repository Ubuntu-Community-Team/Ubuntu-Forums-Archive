---
title: "tar : Exiting with failure status due to previous errors"
date: 2016-06-16
forum: General Help
---

### Post by alain.roger on 2016-06-16
Hi,

whatever i use superuser (sudo) or owner of files (user account), a tar -zcvf backup-home.tar.gz /home/alain generates the same result: 
tar : Exiting with failure status due to previous errors

And i do not have any special report.... what does it mean ?

thx,

---

### Post by slickymaster on 2016-06-16
You can catch tar's command errors filtering its messages to **stdout**```
tar -zcvf backup-home.tar.gz /home/alain > /dev/null
```

---

### Post by alain.roger on 2016-06-16
thx a lot.

It seems that some directories in /home/alain do not allow user:alain to tar file due to lack of permissions :(

---

### Post by slickymaster on 2016-06-17
If you need help setting those permissions right, please post the output of```
ls -l
```

---

