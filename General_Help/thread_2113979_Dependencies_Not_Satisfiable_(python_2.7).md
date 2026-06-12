---
title: "Dependencies Not Satisfiable (python 2.7)"
date: 2013-02-08
forum: General Help
---

### Post by Migrashin on 2013-02-08
I am trying to install a package, but when I try to install it, via either the software center or command line, I get an error about "dependencies not satisfiable python (< 2.7)". 

I know I need python 2.6 for the package to be properly installed. I installed python 2.6 and set it as the default version. However, when I try to install the package it still says dependencies not satisfiable, and that my system is still currently using 2.7.3.

How exactly can I fix this?

---

### Post by GameX2 on 2013-02-08
I had the exact same problem when trying to run an older Blender version.
Have you tried this, in the Terminal?

```
sudo add-apt-repository ppa:fkrull/deadsnakes
sudo apt-get update
sudo apt-get install python2.6 libpython2.6 libjpeg62:amd64 libjpeg62:1386
```

---

### Post by Migrashin on 2013-02-08
Yes I have already installed python 2.6, and it does work on my system. However, the package still sees python 2.7.3 as the installed version.

---

