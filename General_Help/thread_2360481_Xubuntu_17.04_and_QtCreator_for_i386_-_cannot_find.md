---
title: "Xubuntu 17.04 and QtCreator for i386 - cannot find -lgl"
date: 2017-05-05
forum: General Help
---

### Post by chu753chu on 2017-05-05
Xubuntu 17.04 and QtCreator for i386 
does error
> - cannot find -lgl

---

### Post by Xian on 2017-05-05
The libGL.so library is installed from the libgl1-mesa-dev package. 

So let's try to remove your error by installing:

```
sudo apt-get install libgl1-mesa-dev
```

[http://packages.ubuntu.com/zesty/amd64/libgl1-mesa-dev/filelist](http://packages.ubuntu.com/zesty/amd64/libgl1-mesa-dev/filelist)


If already installed you may need to soft link the library with something like:

```
sudo ln -s /usr/lib/x86_64-linux-gnu/mesa/libGL.so /usr/lib/libGL.so
```

---

