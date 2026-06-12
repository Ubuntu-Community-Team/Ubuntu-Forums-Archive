---
title: "/usr/include/ipc.h not present"
date: 2007-02-07
forum: General Help
---

### Post by dabenavidesd on 2007-02-07
Hello:

Im trying to fiure out why there are some files of /usr/src/linux-headers-2.6.17-10/include/asm on /usr/include/asm and some other not and why they are different?

Im trying to compile a c source that uses asm/ipc.h but It didnt find It on the directory asm/ipc.h on /usr/include.

In linux-headers asm/ipc.h does exist and have the line of preprocessor:
#include <asm-generic/ipc.h>

So it redirects the .h

Thanks in advance.
Daniel Benavides

---

