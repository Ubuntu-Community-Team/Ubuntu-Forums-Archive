---
title: "Problem installing Ralink Card Reader Driver RTS5229"
date: 2013-02-13
forum: General Help
---

### Post by theperfectpunk on 2013-02-13
when i try to compile the drivers i get
```

mohit@mohit-HP-Pavilion-g6-Notebook-PC:~/Downloads/Realtek_RTS5229_Linux_Driver_v1.07/rts5229$ sudo make
cp -f ./define.release ./define.h
make -C /lib/modules/3.2.0-37-generic/build/ SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-37-generic'
make[2]: *** No rule to make target `arch/x86/tools/relocs.c', needed by `arch/x86/tools/relocs'.  Stop.
make[1]: *** [archscripts] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-37-generic'
make: *** [default] Error 2

```help plz

---

