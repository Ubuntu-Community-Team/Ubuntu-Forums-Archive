---
title: "Usbtmc"
date: 2014-08-21
forum: General Help
---

### Post by varun8 on 2014-08-21
Hi

I am trying to build the USBTMC drivers for and agilent device i am strucked up with the following error

make    -C /lib/modules/3.2.0-29-generic/build  SUBDIRS=/root/n6705b/usbtmc modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /root/n6705b/usbtmc/usbtmc.o
/root/n6705b/usbtmc/usbtmc.c:1496:2: error: unknown field 'ioctl' specified in initializer
/root/n6705b/usbtmc/usbtmc.c:1496:2: warning: initialization from incompatible pointer type [enabled by default]
/root/n6705b/usbtmc/usbtmc.c:1496:2: warning: (near initialization for 'fops.fsync') [enabled by default]
make[2]: *** [/root/n6705b/usbtmc/usbtmc.o] Error 1
make[1]: *** [_module_/root/n6705b/usbtmc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
make: *** [default] Error 2

As mentioned in the previous threads here i added #include <linux/slab.h> in my source file

Please can any one help me on this.

Thanks
varun.p

---

### Post by stallinux on 2014-11-13
I had the same problem. I found the solution by copying a different usbtmc.c to the directory. I found this version on the server of MIT ([https://stuff.mit.edu/afs/.../usbtmc.c](https://stuff.mit.edu/afs/.../usbtmc.c)) as found by Google:

[https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=9&ved=0CEsQFjAI&url=https%3A%2F%2Fstuff.mit.edu%2Fafs%2Fsipb%2Fcontrib%2Flinux%2Fdrivers%2Fusb%2Fclass%2Fusbtmc.c&ei=PpxkVIu0H8KjgwT6kYToBg&usg=AFQjCNFNFfh7qsMpqN8uTKoGsydNvmipcA&sig2=w34PrCbNserCJiujFNlDmQ&bvm=bv.79189006,d.eXY](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=9&ved=0CEsQFjAI&url=https%3A%2F%2Fstuff.mit.edu%2Fafs%2Fsipb%2Fcontrib%2Flinux%2Fdrivers%2Fusb%2Fclass%2Fusbtmc.c&ei=PpxkVIu0H8KjgwT6kYToBg&usg=AFQjCNFNFfh7qsMpqN8uTKoGsydNvmipcA&sig2=w34PrCbNserCJiujFNlDmQ&bvm=bv.79189006,d.eXY)

after that, the 'make' worked well (Linux Mint [sorry] 16. kernel: 3.11.0-12-generic)

Hope this helps you, or other people having the same problem.

It is a pity those people at Agilent ... erm .. Keysight do not support Linux.

cheers

---

