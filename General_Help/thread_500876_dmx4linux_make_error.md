---
title: "dmx4linux make error"
date: 2007-07-14
forum: General Help
---

### Post by nkwai on 2007-07-14
Hi,
Trying to install dmx4linux version 2.9 (should be for 2.6 kernel), but when I do "make" I get:

```
nkwai@nkwai-laptop:~/dmx4linux-2.9-ba-061001$ make
make -C libs all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/libs'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/libs'
make -C tools all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/tools'
make -C as31-unix all
make[2]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/tools/as31-unix'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/tools/as31-unix'
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/tools'
make -C examples all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/examples'
make -C htmlexamples all
make[2]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/examples/htmlexamples'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/examples/htmlexamples'
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/examples'
make -C drivers all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers'
make -C dmxdev all
make[2]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers/dmxdev'
make -C /lib/modules/2.6.20-16-386/build M=/home/nkwai/dmx4linux-2.9-ba-061001/drivers/dmxdev modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-386'
  Building modules, stage 2.
  MODPOST 1 modules
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-386'
make[2]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers/dmxdev'
make -C devices all
make[2]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices'
make -C misc all
make[3]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/misc'
make -C /lib/modules/2.6.20-16-386/build M=/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/misc modules
make[4]: Entering directory `/usr/src/linux-headers-2.6.20-16-386'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "dmxprop_user_long" [/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/misc/dmxdummy.ko] undefined!
WARNING: "dmxproplist_vacreate" [/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/misc/dmxdummy.ko] undefined!
WARNING: "dmx_find_driver" [/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/misc/dmxdummy.ko] undefined!
WARNING: "dmx_create_family" [/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/misc/dmxdummy.ko] undefined!
make[4]: Leaving directory `/usr/src/linux-headers-2.6.20-16-386'
make[3]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/misc'
make -C i2c all
make[3]: Entering directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c'
make -C /lib/modules/2.6.20-16-386/build M=/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c modules
make[4]: Entering directory `/usr/src/linux-headers-2.6.20-16-386'
  CC [M]  /home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c/dmxi2c.o
/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c/dmxi2c.c: In function ‘i2c_create_universe’:
/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c/dmxi2c.c:232: warning: implicit declaration of function ‘i2c_get_client’
/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c/dmxi2c.c:232: warning: initialisation makes pointer from integer without a cast
/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c/dmxi2c.c: At top level:
/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c/dmxi2c.c:282: error: expected ‘)’ before string constant
make[5]: *** [/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c/dmxi2c.o] Error 1
make[4]: *** [_module_/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.20-16-386'
make[3]: *** [modules] Error 2
make[3]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices/i2c'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers/devices'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.9-ba-061001/drivers'
make: *** [all] Error 2
nkwai@nkwai-laptop:~/dmx4linux-2.9-ba-061001$ 

```

This is the line 282 of the file, can't see what's wrong
```
MODULE_PARM(adapter,"i");
```

Anyone know what to do?

---

### Post by geraldm on 2007-07-14
MODULE_PARM(adapter,"i");

The above is a macro used in compiling the linux kernel.  To compile this correctly you would
have to also compile it within the kernel, as it is using kernel macros.
As a suggestion that I have NOT tried, there is a package called dkms that is used to
compile kernel modules.  I do not know how helpful it is, but it is another approach.

Gerald

---

### Post by nkwai on 2007-07-15
OK I have installed dkms, but don't know how to use it.

---

