---
title: "Installing Labjack"
date: 2007-09-09
forum: General Help
---

### Post by srlevitt on 2007-09-09
Does anyone have any experience of installing the Labjack drivers in Ubuntu? I have downloaded the g++/make tool chain, and the linux source and headers. When I try to make the "labjack.ko" module, make comes back with:

make -C /lib/modules/2.6.15-26-386/build  SUBDIRS=/home/apollo/Apollo/Source/linux-labjack/driver/linux-2.6 modules
make[1]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make: *** [default] Error 2

When I look in that directory, it's completely empty. I am not a Linux expert at all, and it is for that reason I chose Ubuntu - stable OS used by lots of other people I can ask for advice. All I want to do is to get my USB labjack working and carry on with my application development. I don't want to have to recompile the operating system if I can at all help it, and I really wouldn't know how to anyway.

Any pointers gratefully received,
Steve.

---

