---
title: "Setting PATH environment"
date: 2007-04-30
forum: General Help
---

### Post by Ne0z on 2007-04-30
Hi, 

how do i set up PATH environment variable. 

I was given an instruction that says 

"add /directory into your PATH environment variable" 

what does it mean ? and how can i do it ?

---

### Post by bashologist on 2007-04-30
[COLOR="Gray"]#Change the below variable to the new bin directory; e.g. newpath="/data/bin":[/COLOR]
newpath=""
[COLOR="Gray"]#Then paste the following:[/COLOR]
if [ -d "$newpath" ]; then printf "\nif [ -d \"$newpath\" ]; then\n\tPATH=\"$newpath:\$PATH\"\nfi\n" >> ~/.bashrc; PATH="$newpath:$PATH"; fi

---

### Post by Ne0z on 2007-05-01
sorry , im kind of new to ubuntu. so im not really sure what you mean. 

But here is what i've done

i've added this to my /etc/environment file 

> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:
/usr/bin/X11:/usr/games:/tools/arm/4.1.1/gcc-4.1.1-glibc-2.4/arm-none-linux-gnueabi/bin"


in which "/tools/arm/4.1.1/gcc-4.1.1-glibc-2.4/arm-none-linux-gnueabi/bin" was what i added

yet i still get this error when i wan trying to "make" a file

> make: arm-none-linux-gnueabi-gcc: Command not found
  CHK     include/linux/version.h
make[1]: `include/asm-arm/mach-types.h' is up to date.
  CHK     include/linux/utsrelease.h
  CC      arch/arm/kernel/asm-offsets.s
/bin/sh: arm-none-linux-gnueabi-gcc: not found
make[1]: *** [arch/arm/kernel/asm-offsets.s] Error 127
make: *** [prepare0] Error 2


did i set up my PATH environment variables correctly ?

---

### Post by ebash on 2007-05-01
You set the path correctly, but the changes will only take effect in a new shell. Your current shell will not see it. You can make your current shell see the changes by doing:

```
export PATH="${PATH}:/tools/arm/4.1.1/gcc-4.1.1-glibc-2.4/arm-none-linux-gnueabi/bin"
```

---

