---
title: "processor-flags.h file missing"
date: 2013-12-20
forum: General Help
---

### Post by Ashiq_Irphan on 2013-12-20
First let me start with the environment I`m working on
Ubuntu 12.04
```
root@ashiq-Lenovo-G580:~ # uname -r
3.8.0-34-generic
```

I`m working on a program designed to work on kernel 2.6. When I try to run the make command, it returns a lot of missing files. I know that is because the location of the header files are different in kernel 2.6 and kernel 3.8.

What I did was to locate the new location of the missing file and create a symbolic link, so that the program is able to use those header files.

The problem is when the program returned this particular missing file.

```
[LEFT][COLOR=#000000][FONT=Verdana]uapi/asm/processor-flags.h: No such file or directory[/FONT][/COLOR][/LEFT]

```

I found that this particular [LEFT][COLOR=#000000][FONT=Verdana]processor-flags.h to be found in the following locations

```
/usr/include/i386-linux-gnu/asm/processor-flags.h
/usr/src/linux-headers-3.8.0-34/include/uapi/asm-generic/processor-flags.h
/usr/src/linux-headers-3.8.0-34/arch/x86/include/uapi/asm/processor-flags.h
/usr/src/linux-headers-3.8.0-34/arch/x86/include/asm/processor-flags.h
```

I tried creating symbolic links to all the above processor-flags.h

But It returns mutilple erros saying many variables to be undeclared

Is it a good idea to copy the file from kernel 2.6.

Pls suggest me some ideas.
[/FONT][/COLOR][/LEFT]

---

