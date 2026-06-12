---
title: "Maple 7 problem"
date: 2005-10-10
forum: General Help
---

### Post by bogoliubov on 2005-10-10
Hello. I've just installed Maple 7 but I have a problem.
When I try to run it I get the following error:
$ ./xmaple
/usr/local/maple/bin.IBM_INTEL_LINUX/maplew: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I've tried to find an answer, and it seems that the shared library should be in libstdc++2.10-glibc2.2. I have this installed. But now what?

Does anyone have any idea? 

The installation script lets you choose between different architectures, the only one available for x86 was "Redhat/Suse X86", so I choosed this.

---

### Post by annex on 2005-10-10
Is it possible to move to a newer version?  Maple 7 might depend on old libraries.

Maple 9.5 works fine for me.

Not really a solution for 7, sorry.

---

### Post by bogoliubov on 2005-10-10
[QUOTE=annex]Is it possible to move to a newer version?  Maple 7 might depend on old libraries.
Maple 9.5 works fine for me.
Not really a solution for 7, sorry.[/QUOTE]

I was afraid of that answer. The thing is that it's a student license and I'm not sure if the university has a new version yet. They should have, I guess. I don't use all that much, but it's nice to have. I don't want to buy it...

Thanks anyway! :)

---

