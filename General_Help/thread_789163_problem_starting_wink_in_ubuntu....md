---
title: "problem starting wink in ubuntu..."
date: 2008-05-10
forum: General Help
---

### Post by Mia_tech on 2008-05-10
after I upgrade my install from 7.10 to 8.04 wink won't start anymore...this is the error I get.
```
jorge@ubuntu-box:~/wink$ sudo wink
/usr/lib/wink/wink: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

```
I've tried removing it and reinstalling it from synaptic and using apt-get same problem.
any help appriciated

thanks

---

### Post by ibutho on 2008-05-10
Use the package manager to install libexpat1. If its already marked as installed, can you post back the output of running
```
ls -l /usr/lib/libexpat*
```

---

### Post by Mia_tech on 2008-05-10
here's the solution I found cd into the /usr/lib and do a 'sudo ln -s libexpat.so libexpat.so.0'

now the program should start

thanks

---

### Post by ghost_ryder35 on 2008-05-10
congrats on fixing it your self.

---

