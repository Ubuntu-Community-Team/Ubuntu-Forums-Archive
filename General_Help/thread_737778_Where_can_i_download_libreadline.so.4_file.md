---
title: "Where can i download libreadline.so.4 file?"
date: 2008-03-27
forum: General Help
---

### Post by jingqi on 2008-03-27
when i run a software plugin in Ubuntu 7.10, a information jumped out and said, "error while loading shared libraries: libreadline.so.4: cannot open shared object file: No such file or directory
ObjectMapLoadDXFile-Error: Unable to open file!"
I think I might miss the libreadline.so.4 file in my ubuntu.
If so, where can i download it?
help me! thanks

---

### Post by Whiffle on 2008-03-27
[http://packages.ubuntu.com/gutsy/libreadline5](http://packages.ubuntu.com/gutsy/libreadline5)

Should be able to get it from synaptic/apt-get

---

### Post by dcstar on 2008-03-27
> **jingqi said:**
> when i run a software plugin in Ubuntu 7.10, a information jumped out and said, "error while loading shared libraries: libreadline.so.4: cannot open shared object file: No such file or directory
ObjectMapLoadDXFile-Error: Unable to open file!"
I think I might miss the libreadline.so.4 file in my ubuntu.
If so, where can i download it?
help me! thanks

You don't.

libreadline.so.5 is the current version in the (Gutsy) libreadline5 package, whatever plugin you are using is trying to reference an old version.

If you need to, you can make a softlink to it.

---

### Post by jingqi on 2008-03-28
But how can i make the softlink? Pls tell me the details as I am a new one for linux.

---

