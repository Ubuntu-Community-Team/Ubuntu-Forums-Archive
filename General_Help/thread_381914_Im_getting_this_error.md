---
title: "Im getting this error"
date: 2007-03-11
forum: General Help
---

### Post by nikon07 on 2007-03-11
Im getting this error when I go into /etc/init.d/gdm start

```
failed to start X server
```

I can not get to my destop, all I have is a black screen with command line.  I would like to know what I need to type to config this.

---

### Post by raffytaffy on 2007-03-11
sudo dpkg -reconfigure xserver-xorg

then follow the steps to reconfigure it properly.

---

### Post by nikon07 on 2007-03-11
ok  I type n your code this is what I got

dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help
type dpkg -Dhelp
type dpkg --force-help
type dpkg -deb--help

I am not in my desk top Im in a black screen with a command line I cant get to my desktop

I tried to install AIGLX
this is exactly what I did
[https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy")

---

### Post by WW on 2007-03-11
There is an extra space in raffytaffy's command.  The command is **dpkg-reconfigure**.  (I don't know enough about X issues to know if this is, in fact, the best way to deal with your problem.)

---

### Post by bapoumba on 2007-03-11
@ nikon07: moved your thread to "General Help" and yes, **sudo dpkg-reconfigure xserver-xorg**.

---

