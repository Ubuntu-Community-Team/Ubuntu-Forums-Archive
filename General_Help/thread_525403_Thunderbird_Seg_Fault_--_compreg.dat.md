---
title: "Thunderbird Seg Fault -- compreg.dat"
date: 2007-08-14
forum: General Help
---

### Post by T_W on 2007-08-14
Running Feisty.  I just started getting a segfault when starting up thunderbird.

Putting strace on the thunderbird process seems to indicate a problem with the compreg.dat file:

```

open("/home/XXXX/.mozilla-thunderbird/XXX.XXX/compreg.dat", O_RDONLY|O_LARGEFILE) = 5
stat64("/home/XXXX/.mozilla-thunderbird/XXX.XXX/compreg.dat", {st_mode=S_IFREG|0644, st_size=137641, ...}) = 0
mmap2(NULL, 139264, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb71d0000
read(5, "Generated File. Do not edit.\n\n[H"..., 137641) = 137641
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
```

If I delete the compreg.dat and run thunderbird the the program starts up fine.  As part of the startup process, though, it regenerates the compreg.dat and will crash the **next** time I start up.

Looking at the compreg.dat file, there is no obvious corruption.  

This is all with the vanilla Thunderbird 1.5.0.12 direct from the repositories.   No extensions or themes installed.

Thanks for any info.

---

