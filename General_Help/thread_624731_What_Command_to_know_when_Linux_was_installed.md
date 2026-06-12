---
title: "What Command to know when Linux was installed"
date: 2007-11-27
forum: General Help
---

### Post by khmirage on 2007-11-27
My server pc installed Ubuntu Linux Dapper Drake Server ver.

I wonder if there is any command that can tell you when Linux was installed.

Thanks....

---

### Post by ronmarley1 on 2007-11-27
This was all I could find:
[http://ubuntuforums.org/showthread.php?t=520810](http://ubuntuforums.org/showthread.php?t=520810)

---

### Post by mali2297 on 2007-11-27
I remember a discussion about this not too long ago.. :-k


Yes, here it is: :-)
[http://ubuntuforums.org/showthread.php?t=614889](http://ubuntuforums.org/showthread.php?t=614889)

---

### Post by nick_h on 2007-11-27
Look for your oldest initrd file in your boot directory.
```
ls -al /boot
```
I think that the initrd file is created at the time the kernel is installed.  If you haven't updated your initrd files or deleted any old kernels this should give you the install date.

---

### Post by khmirage on 2007-11-30
Reply Thank you :)

---

