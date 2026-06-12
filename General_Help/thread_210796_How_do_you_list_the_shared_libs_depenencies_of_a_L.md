---
title: "How do you list the shared libs depenencies of a Linux executable ?"
date: 2006-07-07
forum: General Help
---

### Post by nmaquet on 2006-07-07
Hello all,

Does someone know how to list the various shared libraries needed by a Linux binary ? 

The purpose would be to identify the runtime dependencies of a little app of mine (so that I can redistribute it and tell people what they might need). 

Thanks for the help !

---

### Post by aysiu on 2006-07-07
I know in Synaptic Package Manager, you can just right-click the package and see the dependencies.

---

### Post by Rui Pais on 2006-07-07
> **nmaquet said:**
> Does someone know how to list the various shared libraries needed by a Linux binary ? 

The purpose would be to identify the runtime dependencies of a little app of mine (so that I can redistribute it and tell people what they might need).

hi,
i think you need either ldd or readelf (read man pages  for details). 
Libraries are listed with -r and -d flag respectively.
Here an example with executable 'gcc': 
```
$ ldd -r `which gcc`
        linux-gate.so.1 =>  (0xffffe000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7dde000)
        /lib/ld-linux.so.2 (0xb7f25000)


$ readelf -d `which gcc` | grep NEEDED
 0x00000001 (NEEDED)                     Shared library: [libc.so.6]
``` 

you can then use dpkg -S to know to which package belongs any lib:
```
$ dpkg -S libc.so.6
libc6: /lib/tls/libc.so.6
libc6-i686: /lib/tls/i686/cmov/libc.so.6
libc6: /lib/libc.so.6
``` 
i don't know if thats what you looking for... (don't know much about the subject)

---

### Post by nmaquet on 2006-07-07
Thanks for your replies, thats exactly what I needed :)

---

