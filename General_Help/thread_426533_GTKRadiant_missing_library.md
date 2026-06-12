---
title: "GTKRadiant missing library"
date: 2007-04-28
forum: General Help
---

### Post by noerrorsfound on 2007-04-28
```
/home/nicholas/Desktop/gtkradiant/radiant.x86: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory
nicholas@nicholas-linux:~$ sudo apt-get install libgtkglext1
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtkglext1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
It says I'm missing the library although it is already installed.

---

### Post by noerrorsfound on 2007-05-04
Maybe I just need to make a symlink to the correct path of the library, but I don't where GTKRadiant expects the library to be and don't know how to find out.

I have both libgtkglext1 libgtkglext1-dev installed, by the way.

---

