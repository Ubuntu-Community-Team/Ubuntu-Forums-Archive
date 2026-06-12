---
title: "C compiler"
date: 2007-04-27
forum: General Help
---

### Post by Balazs_noob on 2007-04-27
Hi everybody i am a new user of Ubuntu :popcorn: 
i just switched from windows :) 

i would have a problem with the GCC C compiler
it dosn't work :( not evan the simplest stuff :(

it writes : 
a.c:1:19: error: stdio.h: No such file or directory
a.c: In function ‘main’:
a.c:4: warning: incompatible implicit declaration of built-in function ‘printf’

so i guess i don't have the standard libaries like stdio.h
how could i fix that ???
i have a AMD 64 + ubuntu 7.04

i hope somebody can help because
i don't want to switch back to Windows :lolflag:

---

### Post by lloyd_b on 2007-04-27
You are missing the package "libc6-dev" which contains those header files.  But I would be concerned about it also being missing something else, so I recommend installing the "build-essential" package, which should contain everything you need to have a working build system.

To install a package, either use one of the graphical package managers (Synaptic, Adept), or in a terminal window:
```
sudo apt-get install {package}
```

Lloyd B.

---

### Post by Balazs_noob on 2007-04-27
Thanks Lloyd B.

it works good now :)

---

