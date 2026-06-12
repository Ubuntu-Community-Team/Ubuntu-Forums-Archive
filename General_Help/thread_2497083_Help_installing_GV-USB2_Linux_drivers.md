---
title: "Help installing GV-USB2 Linux drivers"
date: 2024-04-22
forum: General Help
---

### Post by speedruntrainer on 2024-04-22
Hello everyone.

Recently I've been thinking to switch to Linux. I'm on Ubuntu 22.04 LTS.
I have a capture card called GV-USB2 I used to record my gameplay with. I'm trying to figure out how to install the drivers on Linux, but I'm stuck already...

I'm following [this]("https://gist.github.com/scaramangado/4e09031d782cbad8a4446ba101f43ef7") github guide. I'm stuck on step 2 already...
I installed make and ran it. I'm getting the following error:

ubuntu@ubuntu:~/Desktop/GV-USB2-Driver-master$ make
make -C /lib/modules/6.5.0-18-generic/build M=/home/ubuntu/Desktop/GV-USB2-Driver-master modules
make[1]: Entering directory '/usr/src/linux-headers-6.5.0-18-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
  You are using:           
  CC [M]  /home/ubuntu/Desktop/GV-USB2-Driver-master/gvusb2-snd.o
/bin/sh: 1: gcc-12: not found
make[3]: *** [scripts/Makefile.build:251: /home/ubuntu/Desktop/GV-USB2-Driver-master/gvusb2-snd.o] Error 127
make[2]: *** [/usr/src/linux-headers-6.5.0-18-generic/Makefile:2039: /home/ubuntu/Desktop/GV-USB2-Driver-master] Error 2
make[1]: *** [Makefile:234: __sub-make] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-6.5.0-18-generic'
make: *** [Makefile:7: all] Error 2

What do I need to do and how to install GV-USB2 drivers successfully?

Thanks in advance.

---

