---
title: "Compile failing"
date: 2006-10-14
forum: General Help
---

### Post by crokett on 2006-10-14
Trying to compile a module thusly:

Was first getting an error that '/lib/modules/2.6.15-27-386/build' did not exist so I manually created 'build'.  What directory should the makefile be pointing to?  What packages do I need installed for compiles? 

```
crokett@Hawking:~/downloads/km$ make
make -C /lib/modules/2.6.15-27-386/build M=/home/crokett/downloads/km modules
make[1]: Entering directory `/lib/modules/2.6.15-27-386/build'
make[1]: *** No rule to make target `modules'.  Stop.

```

---

### Post by po0f on 2006-10-14
crokett,

Do you have linux-headers-`uname -r` installed?  Also, post the contents of the Makefile you are trying to use please.

---

### Post by crokett on 2006-10-14
Sigh.  I did not have headers installed so I installed them.  Then I ran the make and it  failed with this error:

```
/home/crokett/downloads/km/km.c:1026: error: ‘PCI_DEVICE_ID_ATI_RADEON_LE’ undec lared here (not in a function)
/home/crokett/downloads/km/km.c:1028: error: ‘PCI_DEVICE_ID_ATI_RADEON_LF’ undec lared here (not in a function)
make[2]: *** [/home/crokett/downloads/km/km.o] Error 1
make[1]: *** [_module_/home/crokett/downloads/km] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [all] Error 2

```

This was a last-gasp to get video capture working in Linux.  This is supposed to be the module to let me do that with my ATI Radeon.  Looks lie the code is buggy and/or not for my system.

---

