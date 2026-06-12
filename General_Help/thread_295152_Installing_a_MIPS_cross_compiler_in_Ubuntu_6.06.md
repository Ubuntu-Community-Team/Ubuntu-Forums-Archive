---
title: "Installing a MIPS cross compiler in Ubuntu 6.06"
date: 2006-11-07
forum: General Help
---

### Post by offspring on 2006-11-07
Hi! I'm trying these days to install a MIPS cross compiler in ubuntu 6.06.
I've downloaded packages binutils-2.17 and gcc-4.1.0. I used the following instructions:

###############################################
BINUTILS:
first configure the makefile :
.configure --target=mips-elf --prefix=/opt/mips-asm” 
then build the binutils by typing : “make all install”

PATH SETTINGS
now set the path for the compiled binaries: “export PATH=$PATH:/opt/mips-asm/bin”


CROSSCOMPILER
now configure the cross-compiler:
“./configure --target=mips-elf --prefix=/opt/mips-asm  --with-gnu-as --with-gnu-ld --verbose --enable-languages=c”
build it: “make all install”
###############################################

Binutils have been installed perfectly. But with gcc there were the following errors:

***********************************************
make[3]: mips-elf-ar: Command not found
make[3]: *** [libgcc.a] Error 127
make[3]: Leaving directory `/home/dimistas/Desktop/gcc-4.1.0/host-i686-pc-linux-gnu/gcc'
make[2]: *** [stmp-multilib] Error 2
make[2]: Leaving directory `/home/dimistas/Desktop/gcc-4.1.0/host-i686-pc-linux-gnu/gcc'
make[1]: *** [all-gcc] Error 2
make[1]: Leaving directory `/home/dimistas/Desktop/gcc-4.1.0'
make: *** [all] Error 2
***********************************************
How can I fix that problem. I've used many things such as:
instead of using --target=mips-elf, I used --target=mips. I've also used the "tconfig.h" file and many HOWTO documents but nothing happened:confused: 

Please help me!

Thanks

Offspring - Punk's not dead!!!

---

### Post by polarislinux on 2008-02-26
Hi,
  I want to know how your question deal with.

---

