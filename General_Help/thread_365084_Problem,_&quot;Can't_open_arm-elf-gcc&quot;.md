---
title: "Problem, &quot;Can't open arm-elf-gcc&quot;"
date: 2007-02-19
forum: General Help
---

### Post by Spectre5 on 2007-02-19
Hello,

I am fairly new to Linux and have started to program on Linux (always used Windows before).  I am having an interesting problem.  I am running xubuntu 6.10.

I installed a compiler for ARM microcontollers in /usr/share/gnuarm-4.0.2 and I added /usr/share/gnuarm-4.0.2/bin to the PATH variable so I can access the compiler.

When I run make on my makefile, I get the following error (arm-elf-gcc is the compiler in /usr/share/gnuarm-4.0.2/bin):

/bin/sh:  Can't open arm-elf-gcc
make: *** [gccversion] Error 2


I have double-checked permissions and I can read and write to the necessary folder/file.  Does anyone have any idea why I am getting this error message and what it means?

Thanks for any help!

---

### Post by Spectre5 on 2007-02-19
> **Spectre5 said:**
> Hello,

I am fairly new to Linux and have started to program on Linux (always used Windows before).  I am having an interesting problem.  I am running xubuntu 6.10.

I installed a compiler for ARM microcontollers in /usr/share/gnuarm-4.0.2 and I added /usr/share/gnuarm-4.0.2/bin to the PATH variable so I can access the compiler.

When I run make on my makefile, I get the following error (arm-elf-gcc is the compiler in /usr/share/gnuarm-4.0.2/bin):

/bin/sh:  Can't open arm-elf-gcc
make: *** [gccversion] Error 2


I have double-checked permissions and I can read and write to the necessary folder/file.  Does anyone have any idea why I am getting this error message and what it means?

Thanks for any help!


Ok, I figured out the problem...the binary I downloaded and unpacked was for a 64 bit machine....so I downloaded an older version which works just fine now!

---

