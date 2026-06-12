---
title: "Problem compiling kernel"
date: 2006-11-01
forum: General Help
---

### Post by zgornel on 2006-11-01
Compiling the kernel (2.6.17, source from edgy repository) gives me this error:
[I]  LD      init/built-in.o
  LD      .tmp_vmlinux1
drivers/built-in.o: In function `ide_wait_not_busy':
(.text+0x657e8): undefined reference to `touch_nmi_watchdog'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.17'
make: *** [debian/stamp-build-kernel] Error 2


[/I]
Anyone has any idea what the problem might be ?

---

### Post by zgornel on 2006-11-03
Has anyone managed to compile the kernel ??

---

