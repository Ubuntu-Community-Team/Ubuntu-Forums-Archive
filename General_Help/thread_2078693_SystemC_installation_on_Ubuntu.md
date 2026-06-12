---
title: "SystemC installation on Ubuntu"
date: 2012-10-31
forum: General Help
---

### Post by MayaS on 2012-10-31
Hello, 

I'm installing  systemc 2.1 on x86 64bit machine, and Ubuntu12.04 OS.
I need this version as a requirement for Metropolis installation (newer versions are implying errors when installing metropolis). 

Upon configuration, I got the following error:
checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized
configure: error: /bin/bash ../config/config.sub x86_64-unknown-linux-gnu failed

I resolved this by replacing the config.sub file with the latest version (downloaded)

But when I do make, I get some errors indicating that quickthreads (qt.h) requires preprocessor definitions for the architecture (e.g. stack alignment).
This was resolved by forcing __i386 in EXTRA_CXXFLAGS in the makefile. Is this valid??

Another error says: ieeefp.h is missing (fatal error: ieeefp.h: No such file or directory  compilation terminated). How can this be resolved?

Thanks

---

### Post by MayaS on 2012-10-31
-

---

