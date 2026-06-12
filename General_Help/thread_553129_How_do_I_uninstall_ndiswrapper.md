---
title: "How do I uninstall ndiswrapper?"
date: 2007-09-17
forum: General Help
---

### Post by krazy1912 on 2007-09-17
How do I uninstall ndiswrapper 1.8 that I downloaded from repository and then reinstall 1.47 from source code?

---

### Post by prince_niceguy on 2007-09-17
Uninstall can be done from the synaptic.

after you download the ndiswapper from the sourceforge. go to source directory and run 

make

sudo make install

modprobe ndiswrapper

ndiswrapper -i <windows driver>

I am not sure you might have to reboot your computer.

---

