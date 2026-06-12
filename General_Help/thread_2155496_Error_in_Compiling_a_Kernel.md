---
title: "Error in Compiling a Kernel"
date: 2013-06-18
forum: General Help
---

### Post by mhfida on 2013-06-18
Hi, 
I am trying to compile a kernel and I am getting the following error

SYSCALL arch/i386/kernel/vsyscall-int80.so
gcc: error: elf_i386: No such file or directory
make[2]: *** [arch/i386/kernel/vsyscall-int80.so] Error 1
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19'
make: *** [debian/stamp/build/kernel] Error 2

I am using gcc version 4.6.3, whereas the version recommended in the manual I am following is 3.4 but I cannot install it i tried 
# apt-get install gcc-3.4 make 
but it cant find it in the database

thanks in advance

---

