---
title: "how to run 32 bit executables on ubuntu 64 bit"
date: 2020-02-24
forum: General Help
---

### Post by kramlevocs on 2020-02-24
Trying to run a 32 bit executable on ubuntu 64. 

get this error: /bin/bash: /exports/toolchains/arm-2011.03/bin/arm-uclinuxeabi-gcc: cannot execute binary file: Exec format error

file command reports: /exports/toolchains/arm-2011.03/bin/arm-uclinuxeabi-gcc: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-, for GNU/Linux 2.2.5, stripped

arch command reports:  x86_64

This file runs fine on another 64 bit x86_64 Centos installation. I'm trying to get this build to work on ubuntu. 

I've seen on ubuntu forums others saying that this should resolve it but it doesn't: 
dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1


What am I doing wrong?

---

### Post by EuclideanCoffee on 2020-02-24
Does this help? [https://stackoverflow.com/questions/14180185/gcc-arm-linux-gnueabi-command-not-found](https://stackoverflow.com/questions/14180185/gcc-arm-linux-gnueabi-command-not-found)

---

### Post by kramlevocs on 2020-02-28
> **EuclideanCoffee said:**
> Does this help? [https://stackoverflow.com/questions/14180185/gcc-arm-linux-gnueabi-command-not-found](https://stackoverflow.com/questions/14180185/gcc-arm-linux-gnueabi-command-not-found)

Thanks Euclid but I had already tried that so further searching found a  post that suggested this which also does not work

[COLOR=#000000]dpkg --add-architecture i386[/COLOR]
[COLOR=#000000]sudo apt-get update[/COLOR]
[COLOR=#000000]sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1

[/COLOR]

---

