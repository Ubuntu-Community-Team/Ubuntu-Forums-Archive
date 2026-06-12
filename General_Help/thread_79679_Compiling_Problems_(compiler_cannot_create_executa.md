---
title: "Compiling Problems (compiler cannot create executables)"
date: 2005-10-20
forum: General Help
---

### Post by jtorrance on 2005-10-20
Hi!

I tried to compile a new version of gmpc ([http://etomite.qballcow.nl/qgmpc-0.12.html](http://etomite.qballcow.nl/qgmpc-0.12.html)) on my Athlon-XP. When running configure I get the error message "C compiler cannot create executables". In the config.log I have the following message:
/lib/libc.so.6: undefined reference to `__libc_stack_end@GLIBC_2.1'
/lib/libc.so.6: undefined reference to `_rtld_global_ro@GLIBC_PRIVATE'
collect2: ld returned 1 exit status

Build-essential is installed.
I tried ro reinstall gcc, tried to use gcc-3.3 and gcc-3.4. I reinstalled the libc and libc-devel packages, the autotools and binutils. I tried a -386 kernel as well. Nothing helps. I also tried to compile some other packages and they all produced the same problem. On my other machine (Pentium 4) it works. I'm using Breezy on both machines, upgraded from Hoary.

Thanks
Kevin

---

### Post by bwainscott on 2005-10-20
I have the same problem so I will be working on a sollution as well

~ B

---

### Post by jtorrance on 2005-10-21
Hi!

Do you have any idea, what else one can try? I'm desperately trying to find a diffenrence between my two machines.
I just tried to compile some module with the module-assistant and that worked flawlessly. However the kernel and therefore the modules are compiled with gcc-3.4.

Kevin

---

### Post by bwainscott on 2005-10-22
From another post on the same topic, try:

apt-get install build-essential

---

### Post by jtorrance on 2005-10-22
Hi!

I already tried that. And I already reinstalled all the packages referenced by build-essential. Unfortunately it didn't help.

Kevin

---

