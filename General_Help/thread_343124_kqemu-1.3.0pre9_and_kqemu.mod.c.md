---
title: "kqemu-1.3.0pre9 and kqemu.mod.c"
date: 2007-01-21
forum: General Help
---

### Post by alterationx10 on 2007-01-21
Greetings all,

I was trying to compile kqemu-1.3.0pre9 and ran into a bit of trouble during the make command.

> mrudolph@saturn:~/Desktop/qemu/kqemu-1.3.0pre9$ make
make -C /lib/modules/2.6.17-10-generic/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/mrudolph/Desktop/qemu/kqemu-1.3.0pre9/kqemu-linux.o
cp /home/mrudolph/Desktop/qemu/kqemu-1.3.0pre9/kqemu-mod-i386.o /home/mrudolph/Desktop/qemu/kqemu-1.3.0pre9/kqemu-mod.o
  LD [M]  /home/mrudolph/Desktop/qemu/kqemu-1.3.0pre9/kqemu.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /home/mrudolph/Desktop/qemu/kqemu-1.3.0pre9/.kqemu-mod.o.cmd for /home/mrudolph/Desktop/qemu/kqemu-1.3.0pre9/kqemu-mod.o
  CC      /home/mrudolph/Desktop/qemu/kqemu-1.3.0pre9/kqemu.mod.o
  LD [M]  /home/mrudolph/Desktop/qemu/kqemu-1.3.0pre9/kqemu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'

it seems the file .kqemu-mod.o.cmd couldn't be found, however it does exist (unlike a similar problem where you have to rename .kqemu.mod.o.cmd to .kqemu-mod.o.cmd)

The most helpful thread I read on it was fairly old. Sorry to repost if this solution has already made it to daylight, but I couldn't seem to find an answer anywhere. I guess this will at least make it easier to find for someone else who is having the problem.

I figured out that if you edit the "Makefile" (line 38 on mine) and find the part that says

> clean:
        rm -f kqemu.o kqemu.ko kqemu-linux.o kqemu-mod.o kqemu.mod.c *~ \
              kqemu-win32.o kqemu-freebsd.o

and change it to something like 
> clean:
        rm -f kqemu.o kqemu.ko kqemu-linux.o kqemu-mod.o *~ \
              kqemu-win32.o kqemu-freebsd.o
#kqemu.mod.c

that the kqemu.mod.c file doesn't get removed somewhere in the middle of the process and kqemu will compile just fine.

Hope it helps.

---

