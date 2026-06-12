---
title: "bash : no such file or directory"
date: 2007-05-10
forum: General Help
---

### Post by olavjunior on 2007-05-10
Before installing feisty I removed a intel fortran folder I didn't use. It was intel in opt (a fortran compiler). 
That was propably not very smart... I thought a fresh install wouldn't miss it, but now, everytime I open a terminal I'm reminded of fortran :S

*bash: /opt/intel/fc/9.1.036/bin/ifortvars.sh: No such file or directory*

Does anyone know how to remove the entry from bash? (which and whrere?)

---

### Post by taurus on 2007-05-10
Could it be in ~/.bashrc?

```
cat ~/.bashrc
```

---

### Post by hartz on 2007-05-10
The fortran environment probably doesn't assume that you're using bash, so there are a few more places where you can look.

These files could all be guilty:
~/.profile (personal .profile file, as suggested by taurus)
~/.bashrc (personal bash profile)
/etc/profile (system-wide user profile)
/etc/bashrc (This file does not necesarily always exist, cannot check ubuntu now.  It is the system-wide bash config file)

---

### Post by olavjunior on 2007-05-11
> **taurus said:**
> Could it be in ~/.bashrc?

```
cat ~/.bashrc
```

Yes, correct! Thanx to you both :)

---

