---
title: "File named &quot;[&quot; in /usr/bin"
date: 2013-12-18
forum: General Help
---

### Post by kend6502 on 2013-12-18
I found a file named "[" in the /usr/bin directory.  Performing a file on this gives:  "[: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x6cd5d3670a4730dab4dd427c82783e01eccf922b, stripped"

Does anyone know if this is a legitimate file?  I've never seen a file name like this.

I'm running a System 76 Bonobo with 13.04.

Thanks....

---

### Post by steeldriver on 2013-12-18
I think it provides the shell test operator - for shells that don't have [ as a builtin

```

man [

help [

```

---

### Post by sisco311 on 2013-12-18
It is part of the coreutils package.  It is similar to the test(1) command (which is also in the coreutils package), but its last argument must    be a literal `]'.

---

### Post by kend6502 on 2013-12-18
OK, thanks for that information.  I'm glad I didn't delete it....

---

### Post by vasa1 on 2013-12-19
Another initial step is to open a terminal and run **type [** or whichever file you want to know a little more about.
```
$ type [
[ is a shell builtin
$ type cd
cd is a shell builtin
$ type [[
[[ is a shell keyword

```

---

