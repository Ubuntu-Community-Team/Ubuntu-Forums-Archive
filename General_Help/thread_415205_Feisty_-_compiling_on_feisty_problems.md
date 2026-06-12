---
title: "Feisty - compiling on feisty problems"
date: 2007-04-20
forum: General Help
---

### Post by sefs on 2007-04-20
After the upgrade (which has a new kernel) this means i have to recompile certain modules like vmware, ndiswrapper etc.  However i am now getting compilation errors on feisty.  What should I do.

Thanks.

---

### Post by rich.bradshaw on 2007-04-20
What are the errors?

---

### Post by sefs on 2007-04-20
all of them look similar to the below....

```


status messges here.... 

make[4]: *** [/usr/lib/parallels/drivers/drv_net/linux/prlnet.o] Error 1
make[3]: *** [_module_/usr/lib/parallels/drivers/drv_net/linux] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
make[1]: *** [vmbridge] Error 2
make[1]: Leaving directory `/usr/lib/parallels/drivers'
make: *** [build] Error 2

```

The compiing looks to be going fine, but when it gets to the make part for anything i try to comiple then the errors start to occur.

It happes when trying to compile the modules for Parallels, Vmware, Ndiswrapper, Truecrypt etc.  

Would you need to see the specific erros for each of the applications listed above?

---

### Post by sefs on 2007-04-20
Ok so in conclusion these erros all seem simply to be applications that are incompatible with the new kernal in feisty. 

For instance downloading and compiling the latest truecrypt and ndiswrapper has worked etc.  VMWare will probably release a version compatible with the new kernal/feisty soon hopefully.

---

### Post by matigol on 2007-04-20
> **sefs said:**
> Ok so in conclusion these erros all seem simply to be applications that are incompatible with the new kernal in feisty. 

For instance downloading and compiling the latest truecrypt and ndiswrapper has worked etc.  VMWare will probably release a version compatible with the new kernal/feisty soon hopefully.

I think the same thing.
There is probably problemes of compatibility.

Have you build-essentials and other ?

---

### Post by Anaea on 2007-04-20
I'm having compiling problems with Feisty too.  I'm trying to get my sound card working but when I get do the make step on the trouble-shooter, the output ends with: 
```

make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2
```

I have the build-essential package installed.  Is there something else I need that I've forgotten?  Or is this just a compatibility issue with the upgrade?

---

### Post by sefs on 2007-04-23
I think these problems will disappear in about 2 - 3 months hopefully when they release updates.  even my samba is now broken.

---

