---
title: "Ubuntu 18.04 LTS - GLIBC 2.29 not found"
date: 2020-04-08
forum: General Help
---

### Post by u666sa on 2020-04-08
[img]https://imgur.com/TkJWVrh.png[/img]

```
~/Desktop/FlexBV-R1145-linux &#57520; ./flexbv./flexbv: /lib/x86_64-linux-gnu/libm.so.6: version `GLIBC_2.29' not found (required by ./flexbv)

```

Somebody download [https://pldaniels.com/flexbv/downloads.php](https://pldaniels.com/flexbv/downloads.php) and try running it on Ubuntu 18.04 LTS.  That error.
Getting .deb file for glibc 2.29 is a no go since it has dependancies.  

Please suggest a work around.

---

### Post by mörgæs on 2020-04-08
I'm not sure what the question is. 

If you need glibc in version 2.29 or above I recommend a clean install of Buntu 19.10 which includes glibc 2.30.

---

### Post by u666sa on 2020-04-10
Bad recommendation.

I need GLIBC 2.29 in Ubuntu 18.04.

---

### Post by Impavidus on 2020-04-10
Complain to whoever provided that executable. This is really poor software distribution.

A compiled and dynamically linked executable needs a specific version of the library. The normal way on Linux is to compile the program for a specific release of the operating system. Alternatively, a statically linked binary or the source code could be distributed.

You can install multiple versions of a shared object file side by side, but it's a nightmare, which is why package management was invented. So you could have both libc6 2.27 and libc6 2.29, but not so easily from the deb package, as that would cause a conflict with your existing libc6. Maybe if you just extract the actual .so file from the package? Or compile and statically link libc6 2.29 yourself? It won't be easy.

---

