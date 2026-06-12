---
title: "Kernel 2.4 issues"
date: 2006-07-06
forum: General Help
---

### Post by Buchuki on 2006-07-06
Hello,

I need to port a development kernel module that was developed on the 2.4 kernel about two years ago to kernel 2.6. The first step for me has been to try to get a working 2.4 kernel so I can compile and test the original code. This has been a lot more of a headache than I've imagined.

I've tried various options including qemu, user mode linux, and installing and/or compiling a live kernel. I've tried both dapper and breezy installs of k/ubuntu with no luck. Each has its own problems, for dapper there are kernel-image-2.4.27 packages, but I get a VFS kernel panic on booting, for breezy no such package exists, and trying to compile it gives me compilation errors, I believe because of gcc 4. I can't figure out how to make it compile with gcc 3 properly, I tried 'alias gcc=gcc3.3' but it gave the same errors. I have similar errors when trying to compile a UML patched 2.4 kernel.

I'm at wit's end, all I want is a 2.4 kernel in my ubuntu install, somehow! Does anyone have any suggestions? I'm thinking I may need to install Warty into qemu somehow, but then I'm guessing I won't have a hope of putting the 2.6 kernel beside it. Is there a magic hidden 2.4 package out there somewhere I can try? I didn't think it should be this hard.

Thanks very much for any insight.

Dusty

---

### Post by tseliot on 2006-07-06
[QUOTE=Buchuki]Hello,

I need to port a development kernel module that was developed on the 2.4 kernel about two years ago to kernel 2.6. The first step for me has been to try to get a working 2.4 kernel so I can compile and test the original code. This has been a lot more of a headache than I've imagined.

I've tried various options including qemu, user mode linux, and installing and/or compiling a live kernel. I've tried both dapper and breezy installs of k/ubuntu with no luck. Each has its own problems, for dapper there are kernel-image-2.4.27 packages, but I get a VFS kernel panic on booting, for breezy no such package exists, and trying to compile it gives me compilation errors, I believe because of gcc 4. I can't figure out how to make it compile with gcc 3 properly, I tried 'alias gcc=gcc3.3' but it gave the same errors. I have similar errors when trying to compile a UML patched 2.4 kernel.

I'm at wit's end, all I want is a 2.4 kernel in my ubuntu install, somehow! Does anyone have any suggestions? I'm thinking I may need to install Warty into qemu somehow, but then I'm guessing I won't have a hope of putting the 2.6 kernel beside it. Is there a magic hidden 2.4 package out there somewhere I can try? I didn't think it should be this hard.

Thanks very much for any insight.

Dusty[/QUOTE]
Download the vanilla sources from this website:
[http://www.kernel.org/](http://www.kernel.org/)

and instead of the export CC thing you can temporarily make a symbolic link to the compile:
Make sure you have the right compiler (3.3 ?) for the kernel 2.4 (which I've never tried)
```
sudo apt-get install gcc-3.3
```
```
sudo ln -sf /usr/bin/gcc-3.3 /usr/bin/gcc
```

And after the compilation finishes, restore the symlink to gcc-4.0:
```
sudo ln -sf /usr/bin/gcc-4.0 /usr/bin/gcc
```

If you need a guide to kernel compilations:
[http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)

---

### Post by Buchuki on 2006-07-06
hmm.... thanks. I tried it, but I'm still getting a compile error... I think its a different error, however. This may be because I was trying gcc 3.4 instead of 3.3 before.

```

make[2]: Entering directory `/usr/src/linux-2.4.24/arch/i386/kernel'
gcc -D__KERNEL__ -I/usr/src/linux-2.4.24/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i686   -nostdinc -iwithprefix include -DKBUILD_BASENAME=process  -c -o process.o process.c
process.c: In function `machine_restart':
process.c:427: warning: use of memory input without lvalue in asm operand 0 is deprecated
{standard input}: Assembler messages:
{standard input}:809: Error: suffix or operands invalid for `mov'
{standard input}:810: Error: suffix or operands invalid for `mov'
{standard input}:904: Error: suffix or operands invalid for `mov'
{standard input}:905: Error: suffix or operands invalid for `mov'
{standard input}:946: Error: suffix or operands invalid for `mov'
{standard input}:947: Error: suffix or operands invalid for `mov'
{standard input}:949: Error: suffix or operands invalid for `mov'
{standard input}:961: Error: suffix or operands invalid for `mov'
make[2]: *** [process.o] Error 1
make[2]: Leaving directory `/usr/src/linux-2.4.24/arch/i386/kernel'
make[1]: *** [_dir_arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.4.24'
make: *** [stamp-build] Error 2

```

Perhaps I can fix this by turning off a kernel option or maybe I need another option. Would it be possible someone has a kernel2.4 package that would run on dapper or breezy?

Thanks again,
Dusty

---

### Post by woot on 2006-07-10
Buchuki: you have to patch your kernel source to get rid of the mov error, I' ve been trying to compile my own 2.4 kernel aswell yesterday and o boy... I thought following some guide..piece of cake...right on :)

I used gcc 2.95, but maybe 3.3 is fine aswell

now for the mov error:(perhaps you can google around but you should end up with this patch I think)
you need to download and apply the following patch (as root)
root:/usr/src/linux# wget ww.kernel.org/pub/linux/devel/binutils/linux-2.4-seg-4.patch
root:/usr/src/linux# patch -Np1 -i linux-2.4-seg-4.patch

Allthough one file he couldnt patch as it simply wasnt there...so i skipped that one

But in the end when i boot from my new kernel I get starting pcmcia services failed and end up in textmode.

---

### Post by Buchuki on 2006-07-10
Thanks for the information, that will probably work for my purposes. I ended up making it work by installing a Hoary iso into qemu and using kernels and compilers from there, but this would probably have been easier.

Thanks!

Dusty

---

### Post by woot on 2006-07-10
what kernel dus hoary have as it is installed?

---

### Post by Buchuki on 2006-07-15
Hoary is running 2.6.10 by default, but I was able to find a 2.4.26 package online somewhere. I've realized I have to recompile both kernels in order to play with the sources (I thought I was just writing a kernel module at first, but it turns out I have to hack some system calls too). I'm experimenting with the compiler right now, hopefully they'll both compile for me without giving me any headaches.

Wouldn't that be neat? ;-)

Dusty

---

### Post by tseliot on 2006-07-15
BTW now I remmber that one of the (few) distros which use kernel 2.4-x by defaul yet is Slackware

---

### Post by rick_1010 on 2006-09-30
Hi, I'm trying to do the same thing as I need the 2.4.26 kernel for an openmosix cluster. I have followed all the steps so far but now I am getting stuck on this error:

"Version requires old depmod, but couldn't run /sbin/depmod.modutils: No such file or directory"

--I realize that this is some issue with the depmod, does Dapper Drake not have a depmod by defualt? I've never done a kernel compile before so I am not familiar with depmod but I will keep looking into it, if anyone has more information on this please post.

Thanks

---

### Post by judson on 2007-12-15
To fix:

sudo apt-get install gcc-2.95
Get the kernel sources.
In the Makefile at:
/usr/lrc/linux-.2.4.xx/ Makefile 
change gcc to gcc-2.95

If you get this error:
Error: suffix or operands invalid for `mov'

Apply this patch:
[http://www.kernel.org/pub/linux/devel/binutils/linux-2.4-seg-4.patch](http://www.kernel.org/pub/linux/devel/binutils/linux-2.4-seg-4.patch)
[http://www.kernel.org/pub/linux/devel/binutils/linux-2.6-seg-5.patch](http://www.kernel.org/pub/linux/devel/binutils/linux-2.6-seg-5.patch)

HTH.

---

### Post by judson on 2007-12-15
For the depmod issue:

sudo ln -s /sbin/depmod /sbin/depmod.modutils

HTH.

Jud

---

