---
title: "Building Truecrypt under edgy eft (6.10)"
date: 2007-01-06
forum: General Help
---

### Post by taboom on 2007-01-06
When I try to compile (build) Truecrypt I get:

```
Checking build requirements...
Building kernel module... Done.
Building truecrypt... In file included from ../../Crypto/Aesopt.h:144,
                 from ../../Crypto/Aescrypt.c:33:
../../Common/Endian.h:43:5: error: #error Byte order cannot be determined (BYTE_ORDER undefined)
make: *** [../../Crypto/Aescrypt.o] Error 1
Error: Failed to build truecrypt
```

Has anyone got an idea where this error comes from and how I can fix it to get Truecrypt compiled and installed?

I use 3v1n0's suspend2 enabled kernel ([http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)) but the same problem also exists on the normal kernel for me. What I use is: Ubuntu 2.6.17-2.2.9+3v1ubuntu1-generic

---

### Post by Njall on 2007-01-06
There are other threads about building TrueCrypt here.  I believe you have to have the kernel source, including headers, on your system.  Not being able to get a value for byte order, " (BYTE_ORDER undefined)", sure looks like you're probably missing the header files.

Good luck!

- Nelson

---

### Post by taboom on 2007-01-06
I have tried to follow different guides for this, and have installed headers and the source as recommended but I still have this problem... I haven't noticed anywhere else that this would have been a problem and that's what bothers me. 

If I don't install some dependencies or kernel sources I get errors other people also have gotten.

---

### Post by taboom on 2007-01-24
SOLVED

I'm replying myself to report how to solve this.

Just don't try to compile truecrypt on a FAT partition.

See bjorn's post at truecrypt's forum - [http://forums.truecrypt.org/viewtopic.php?t=5220#25184](http://forums.truecrypt.org/viewtopic.php?t=5220#25184)

---

