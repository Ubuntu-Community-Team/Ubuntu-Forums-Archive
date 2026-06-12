---
title: "Kbuild problem when trying to build module with make: cannot find Kbuild.include"
date: 2014-01-12
forum: General Help
---

### Post by Purnish_Dave on 2014-01-12
Hi,

This isn't an Ubuntu specific question but just thought of asking for advice

I am trying to build a simply helloworld module into the kernel.

I have a file called helloworldk.c with init and exit functions to be invoked with insmod and rmmod.

My kernel source tree is in /usr/src/linux-3.12.7

I created a Makefile with the line
```
    obj-m :=helloworldk.o 

```
and am executing the command

```
    make -C /usr/src/linux-3.12.7 M='pwd' modules 

```
However, I get the following output

```
    make: Entering directory `/usr/src/linux-3.12.7'
Makefile:323: /usr/src/linux-3.12.7/scripts/Kbuild.include: No such file or directory
Makefile:579: /usr/src/linux-3.12.7/arch/x86/Makefile: No such file or directory
/bin/bash: /usr/src/linux-3.12.7/scripts/gcc-goto.sh: No such file or directory
make: *** No rule to make target `/usr/src/linux-3.12.7/arch/x86/Makefile'.  Stop.
make: Leaving directory `/usr/src/linux-3.12.7' 

```

What am I doing wrong?

---

