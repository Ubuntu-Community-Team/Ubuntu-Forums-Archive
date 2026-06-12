---
title: "pass options to gcc linker only when needed."
date: 2014-02-07
forum: General Help
---

### Post by krafczyk-matthew on 2014-02-07
Hi, I'm trying to force gcc to use a specific linker at all times. I've created a script to pass the -Wl,--dynamic-linker=/path/to/linker option to gcc every time I call it.

The problem is that gcc tries to invoke this linker even when I'm not really trying to link resulting in an error since it can't find the main function. So if I call

```
gcc -Wl,--dynamic-linker=/path/to/linker -v
```

gcc will report an error since it tries to compile nothing.

Is there a way I can tell gcc to use a specific linker, and not have it try to link everything?

---

### Post by krafczyk-matthew on 2014-02-07
I think I've solved this.

I wound up using the gcc specs file. Below is the specs file I wound up using.

```
%rename cpp old_cpp


*cpp:
-I%:getenv(SYSROOT /include) %(old_cpp)


%rename lib old_lib


*lib:
-L%:getenv(SYSROOT /usr/lib64/) -rpath=%:getenv(SYSROOT /lib64) --dynamic-linker=%:getenv(SYSROOT /lib64/ld-linux-x86-64.so.2) %(old_lib)

```

I can then pass the specs file to gcc like gcc -specs=/path/to/specs/file <other options>

you can read about the specs file here: [http://gcc.gnu.org/onlinedocs/gcc/Spec-Files.html](http://gcc.gnu.org/onlinedocs/gcc/Spec-Files.html)

---

