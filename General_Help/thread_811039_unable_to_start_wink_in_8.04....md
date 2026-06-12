---
title: "unable to start wink in 8.04..."
date: 2008-05-28
forum: General Help
---

### Post by Mia_tech on 2008-05-28
I've installed wink, but I get error:
```
jorge@ubuntu-lap:~$ sudo wink
/usr/lib/wink/wink: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

```
I found a guide that suggested to create a symbolic link in /usr/lib:
```
sudo ln -s libexpat.so libexpat.so.0

```
but after making all this changes still didn't work

any help appreciated..

thanks

---

### Post by sizzam on 2008-05-29
The correct symlink to make this work is (assuming you have the 'libexpat1' package installed):
```
sudo ln -s /usr/lib/libexpat.so.1 /usr/lib/libexpat.so.0
```

I'll report this broken package (wink).

---

### Post by sizzam on 2008-05-29
Just checked, the bug was [already reported]("https://bugs.launchpad.net/ubuntu/+source/wink/+bug/185868").

---

