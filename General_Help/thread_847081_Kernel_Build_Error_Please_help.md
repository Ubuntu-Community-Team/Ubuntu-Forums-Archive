---
title: "Kernel Build Error: Please help"
date: 2008-07-02
forum: General Help
---

### Post by karthikb23 on 2008-07-02
Hi,
On trying to compile the kernel on my hoary (5.04), i get the following error on doing either:
'make clean' or 'make bzImage'

  CHK     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
  UPD     include/linux/version.h
  CHK     include/asm-i386/asm_offsets.h
/bin/sh: arch/i386/kernel/asm-offsets.s: No such file or directory
  UPD     include/asm-i386/asm_offsets.h
mv: cannot stat `include/asm-i386/asm_offsets.h.tmp': No such file or directory
make: *** [include/asm-i386/asm_offsets.h] Error 1

./include/asm-sparc/ptrace.h: * The asm_offsets.h is a generated file, so we cannot include it.
./include/asm-sparc/ptrace.h:/* #include <asm/asm_offsets.h> */


  CHK     include/linux/version.h
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2

I tried creating empty files for 'asm_offsets.h' or 'asm-offsets.s', but to no avail.

PLease help if you can :confused:

Thanks in advance!

---

### Post by PmDematagoda on 2008-07-02
Where did you get the kernel sources from? Also did you make sure if the source you downloaded is not corrupted in any way?

---

### Post by karthikb23 on 2008-07-02
thanks.
i downloaded the sources from teh Hoary Alternate install CD itself.

I just want to mke sure its no problem from my side.

I already had a lot of issues setting up 'menuconfig', with lots of packages/dependencies missing from the hoary CD and had to pick up stuff from here n there to get it to work.

I really wonder how the senior Ubuntu users (who used Hoary) performed kernel compilation :( :confused:

---

### Post by PmDematagoda on 2008-07-02
Well, I am not sure if you know this but Ubuntu Hoary is long gone(so to say), why aren't you using Ubuntu Hardy?

About the kernel, did you try compiling a vanilla of the kernel in Hoary? You can get the vanilla kernel from [here]("http://www.kernel.org/").

---

### Post by karthikb23 on 2008-07-03
Thanks PM :)

yes i know Hoary is long gone, but i want to use it as a test-box, maybe see how hard things really were :) and then switch to hardy n see t difference

---

