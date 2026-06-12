---
title: "gcc errors during Kernel Compile"
date: 2007-02-09
forum: General Help
---

### Post by Inhumane on 2007-02-09
I'm trying to recompile a kernel, but during the opteration, I keep getting this error:
> kernel/sched.c:7013: internal compiler error: in pop_scope, at c-decl.c:855
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[2]: *** [kernel/sched.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

It happens at random times, sometimes right near the end, sometimes right at the start, and this is very annoying as I have to recompile the kernel several times because I am messing with a few settings. It usually takes around 15 (!) recompile tries before it goes through a whole compile:confused:

---

### Post by po0f on 2007-02-09
Inhumane,

```
[FONT="Courier New"]The bug is not reproducible, so it is likely a hardware or OS problem.[/FONT]
```

Either your hardware is overheating during the compile, or you have faulty memory.  To check your memory, boot up and in GRUB's menu, choose the 'memtest86+' option.

---

### Post by Inhumane on 2007-02-09
Just ran it for a pass and a half, no errors. And it isn't a bad OS install either because this is about the third time I've reinstalled it in a few days

---

### Post by lamego on 2007-02-09
Like, is is likely to be an hardware related problem. I would run at least the memcheck utility.

---

