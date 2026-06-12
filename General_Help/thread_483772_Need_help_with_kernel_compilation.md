---
title: "Need help with kernel compilation"
date: 2007-06-25
forum: General Help
---

### Post by Dinchamion on 2007-06-25
Though I posted this in [this thread](http://ubuntuforums.org/showthread.php?t=56835), but it quickly got to page 4 so I thought I start a new one instead.

My problem is that I followed the guide above step by step, but at the end, when it came to actually compiling the kernel I get the following error:

```
  AS      arch/x86_64/lib/putuser.o
  AS      arch/x86_64/lib/rwlock.o
  AS      arch/x86_64/lib/thunk.o
  CC      arch/x86_64/lib/usercopy.o
  AR      arch/x86_64/lib/lib.a
  GEN     .version
  CHK     include/linux/compile.h
dnsdomainname: Unknown host
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
ubuntu/built-in.o:(.bss+0x10588): multiple definition of `debug'
arch/x86_64/kernel/built-in.o:(.kprobes.text+0x3d0): first defined here
ld: Warning: size of symbol `debug' changed from 333 in arch/x86_64/kernel/built-in.o to 4 in ubuntu/built-in.o
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2
```

Now I'm not completely new to kernel compilation, and I tried various things, but nothing seems to do anything, I always get this exact same error message, and now I'm completely cluesless.

Any help would be appreciated!

---

