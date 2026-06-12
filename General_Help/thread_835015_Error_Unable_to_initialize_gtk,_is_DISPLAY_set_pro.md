---
title: "Error: Unable to initialize gtk, is DISPLAY set properly?[/code]"
date: 2008-06-20
forum: General Help
---

### Post by anjanesh on 2008-06-20
I downloaded FileZilla_3.0.11_x86_64-linux-gnu.tar.bz2 and did
```
root@AL-Linux:/opt# tar -jxf FileZilla_3.0.11_x86_64-linux-gnu.tar.bz2
root@AL-Linux:/opt# cd FileZilla3/bin
root@AL-Linux:/opt/FileZilla3/bin# ./filezilla
Error: Unable to initialize gtk, is DISPLAY set properly?
```

Any idea how to get FileZilla running ?

Thanks

---

### Post by sdennie on 2008-06-20
Is there a reason you can't use filezilla from the repos?  At the very least it's available for 32bit.  To install it:

```

sudo apt-get install filezilla

```

---

### Post by anjanesh on 2008-06-20
1. I didnt know FileZilla exited in Add/Remove - its only available when you select **All Open Source Applications** and not **Supported Applications**. I just now added it and FileZilla 3.07.1_x86_64 version is installed and working.

2. Why didnt the previous shell command work anyway ?

---

### Post by sdennie on 2008-06-20
Looking at the original post, it looks like you did a "sudo -i" before trying to run the app.  In that case, the parent shell variables were discarded (including $DISPLAY) so, the app wasn't able to start because it didn't know where to display it.

---

### Post by anjanesh on 2008-06-20
Wow ! Thank you so much.
I just logged off root and went back to normal user mode and it worked !

Weird - so if I wanted to run as root ... ?

---

### Post by sdennie on 2008-06-20
> **anjanesh said:**
> 
Weird - so if I wanted to run as root ... ?

I would avoid running anything as root unless it's absolutely needed.  Among other things, a common problem is to have dotfiles in your home directory become owned by root after running a GUI app as root and it can produce strange results that are hard to diagnose.

---

