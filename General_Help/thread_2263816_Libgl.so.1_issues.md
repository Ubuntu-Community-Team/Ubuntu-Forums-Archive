---
title: "Libgl.so.1 issues"
date: 2015-02-03
forum: General Help
---

### Post by cybuss on 2015-02-03
Hello i've been having problems with the libgl.so.1
i have installed the binary nvidia driver 343

and when ever i try to run skype or other programs that use it gives me this

ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
/usr/bin/skype: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64

so obivously maybe i only have a single libgl.so.1,

cybuss@Vault:~$ ldconfig -p | grep libGL.so.1
	libGL.so.1 (libc6,x86-64) => /usr/lib/libGL.so.1

cybuss@Vault:~$ sudo  find / -name libGL.so.1
/usr/lib32/libGL.so.1
/usr/lib/i386-linux-gnu/primus/libGL.so.1
/usr/lib/libGL.so.1

so it appears as though i have 3 lib.gl.so.1, perhaps its not properly symlinked?

---

