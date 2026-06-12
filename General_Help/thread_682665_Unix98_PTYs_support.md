---
title: "Unix98 PTYs support???"
date: 2008-01-30
forum: General Help
---

### Post by Guardian-Mage on 2008-01-30
I wasn't sure where to post this so I decided to post it here. I am building a LFS system using the dev book and I am on page:

[http://www.linuxfromscratch.org/lfs/view/development/chapter06/binutils.html](http://www.linuxfromscratch.org/lfs/view/development/chapter06/binutils.html)

and I get this error:
  root:/source/binutils-2.18# expect -c "spawn ls"
  spawn ls
  The system has no more ptys.  Ask your system administrator to create more.
      while executing
  "spawn ls"

I am using Kubuntu 7.10 and I just want to know if Kubuntu supports Unix98 PTYs

---

### Post by Guardian-Mage on 2008-01-30
I fixed part of the error be leaving my chroot enviroment and executing 
mount --bind /dev $LFS/dev

and now i get this error:
Segmentation fault (core dumped)

---

### Post by Kopachris on 2008-01-31
I have the same problem as you.  The problem is the same in both KDE and GNOME.  I followed the instructions in the FAQ, then mounted /dev and now it says
```

root:/# expect -c "spawn ls"
spawn ls
Segmentation fault (core dumped)

```
Somebody please help.

---

