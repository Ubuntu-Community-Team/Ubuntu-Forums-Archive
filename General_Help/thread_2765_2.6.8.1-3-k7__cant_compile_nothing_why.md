---
title: "2.6.8.1-3-k7  cant compile nothing why ?"
date: 2004-10-31
forum: General Help
---

### Post by ToWAH on 2004-10-31
I just installed k7 kernel 2.6.8.1-3-k7

and now i cant compile nothing :| 
trying to xine 

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
arggg 

how need it ?

---

### Post by ToWAH on 2004-10-31
Ok i resolved it

---

### Post by sebast on 2004-11-25
How did you resolved it? I have the same problem.

---

### Post by p!=f on 2004-11-25
[QUOTE=sebast]How did you resolved it? I have the same problem.[/QUOTE]
Looks like you have no c++ compiler.
```

sudo apt-get install g++

```

---

### Post by sebast on 2004-11-25
Ok,

That's right, installing G++ with synaptic resolved that.

---

### Post by plasmo on 2004-11-25
apt-get build-essential  8-)

---

