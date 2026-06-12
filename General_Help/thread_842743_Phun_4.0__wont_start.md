---
title: "Phun 4.0  wont start"
date: 2008-06-27
forum: General Help
---

### Post by Crypty on 2008-06-27
I can't start the new version of phun. This is what terminal spits out...


```
steve@steve-laptop:~/Desktop/PhunBeta4$ ./phun
./phun.bin: error while loading shared libraries: libGLEW.so.1.3: cannot open shared object file: No such file or directory

```

I already have libglew 1.5 so i'm not sure what to do. Any help is appreciated.

---

### Post by entropy_ on 2008-06-27
It is because phun was compiled against the old version of libGLEW. The best thing to do is to install the old version, but you can just create a symlink to the newer version. Try ```
sudo ln /usr/lib/libGLEW.so.1.5 /usr/lib/libGLEW.so.1.3
```

---

