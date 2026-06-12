---
title: "How to install Free Pascal and Lazarus?"
date: 2005-04-26
forum: General Help
---

### Post by aluisiuz on 2005-04-26
I downloaded&installed fp-compiler_1.0.4-2_i386.deb and fp-units-rtl_1.0.4-2_i386.deb manually (latest stable version). Then I extracted the actual Lazarus version and made 'make clean all'. Now the following error appears:

```
/bin/rm -f units/i386/linux/alllclunits.ppu
ppc386 -gl -Fu. -Funonwin32 -Fuwidgetset -Fiinclude -FUunits/i386/linux -Fl/usr/lib/gcc-lib/i486-linux/3.3.5 -Fl/usr/X11R6/lib -Fl/usr/local/lib -di386 alllclunits.pp
Free Pascal Compiler version 1.0.4 [2001/08/31] for i386
Copyright (c) 1993-2000 by Florian Klaempfl
Target OS: Linux for i386
Compiling alllclunits.pp
Panic : Internal compiler error, exiting.
syslinux.pp(31,1) Fatal: Internal error 9999
make[1]: *** [alllclunits.ppu] Fehler 1
make[1]: Verlasse Verzeichnis »/src/lazarus/lcl«
make: *** [lcl] Fehler 2
```

What do I wrong?

Ciao,
aluisiuz

---

