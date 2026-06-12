---
title: "Boot UP Manager or substitute for"
date: 2018-04-27
forum: General Help
---

### Post by SuperFreak on 2018-04-27
I wonder if it is possible to install Boot-Up Manager on 18.04. If not is there another program that will define timing of programs during boot process. (Start Up Applications won't do it for my situation)

---

### Post by TheFu on 2018-04-27
Perhaps ... 
```
$ systemd-analyze blame
```
is what you seek?  It is part of systemd systems.  There is a way to get some html/graphics from it.  IDK how.

---

### Post by SuperFreak on 2018-04-27
Thanks

I am trying to get a program to lanch on Boot before another.
```
systemd-analyze blame
```
Shows me boot order and indicates when one program starts but not the other. BUM was a simple was of ordering things

---

### Post by TheFu on 2018-04-27
With systemd, you can specify dependencies. [https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers) is the Ubuntu info, but systemd works the same across distros, so if you find a better/clearer page with Arch or Debian or Fedora, the ideas will be the same.  Only thing that might change slightly are where files are placed.  IDK.

---

### Post by SuperFreak on 2018-04-27
I found a deb package for BUM but get this error when installing through GDebi

```
error :dependency is not satisfiable:sysc-rc
```

---

