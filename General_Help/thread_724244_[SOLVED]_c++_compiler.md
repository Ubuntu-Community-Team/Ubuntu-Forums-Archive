---
title: "[SOLVED] c++ compiler"
date: 2008-03-14
forum: General Help
---

### Post by Rytron on 2008-03-14
Hi,
Is there a good c++ compiler for Ubuntu 7.10?

---

### Post by x1a4 on 2008-03-14
g++

---

### Post by Rytron on 2008-03-14
in synaptic it is already installed.
how do I start it?

---

### Post by taurus on 2008-03-14
Make sure you install the build-essential package, not just g++, since you need all the libraries that the compiler needs to compile something from source.

```
sudo apt-get update
sudo apt-get install build-essential
g++ *filename.cpp*
```

---

### Post by FluffyElmo on 2008-03-14
If you are looking for an IDE instead of just the compiler, Anjuta or KDevelop would be good places to start. Both are available in Synaptic.

---

