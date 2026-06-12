---
title: "How do I create a .deb of a compiled app?"
date: 2008-05-23
forum: General Help
---

### Post by denzilla on 2008-05-23
With some help, I am able to compile SDLMAME but how do I create a .deb package from the compilation? Can the .deb be created after the compilation is done or is there some sort of compile-time command I need to enter? Thanks all :)

PS: Hardy 8.04 is my OS

---

### Post by drs305 on 2008-05-23
You can make a deb file during installation. Instead of the usual last command of 'make install' you would use 'checkinstall'.

Normally, the commands for compilation are variations of this (read the INSTALL file in the package):
```

./configure
make
make install
```

To make a deb package:
```

./configure
make
sudo checkinstall
```

Checkinstall is available in synaptic. 

Search google for sites that explain it or type:
```
man checkinstall
```
Here is one link:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

