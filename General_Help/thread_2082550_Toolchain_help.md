---
title: "Toolchain help"
date: 2012-11-09
forum: General Help
---

### Post by Evolutionmods on 2012-11-09
so im compiling linux kernels and im having some minor problems.
Im sorry if this is not posted in the right place, i did a search for similar post with nothing.

im getting this error 

```
 /home/ubuntu/kernels/liberty-stock/prebuilt/linux-x86/toolchain/arm-eabi-4.4.3/bin/arm-eabi-gcc-4.4.3gcc:  No such file or directory
```Im using that binary but it doesnt have the gcc on the end of it.

i have added the right classpath to the bash.rc

```
export PATH=$(pwd)/prebuilt/linux-x86/toolchain//bin:$PATH
export ARCH=arm
export SUBARCH=arm
export CROSS_COMPILE=arm-eabi- 

```and also added it to the make file just to be sure.

```
export KBUILD_BUILDHOST := $(SUBARCH)
ARCH        ?= $(SUBARCH)
CROSS_COMPILE    ?= /home/ubuntu/kernels/liberty-stock/prebuilt/linux-x86/toolchain/arm-eabi-4.4.3/bin/arm-eabi-4.4.3
CROSS_COMPILE    ?= $(CONFIG_CROSS_COMPILE:"%"=%)
```Im wonder what would add the gcc to the end of it to make it look for a binary that isnt there? please dont be to brutal on me 

thanks guys.

---

### Post by Evolutionmods on 2012-11-10
All fixed!!

---

### Post by Sk13 on 2013-04-17
Hello Evolutionmods,

Can you please share how did u resolve the problem?

Thanks!

---

### Post by Evolutionmods on 2013-04-18
> **Sk13 said:**
> Hello Evolutionmods,

Can you please share how did u resolve the problem?

Thanks!

It was the arm-eabi-     extension. i had it at arm-linux-androideabi-          
just follow the extension thats in the bin folder of your toolchain

Also ...you dont need to add the path to the bash.rc if your not carefull you can jack up the class path for your system

---

