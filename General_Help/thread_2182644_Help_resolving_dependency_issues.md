---
title: "Help resolving dependency issues"
date: 2013-10-21
forum: General Help
---

### Post by mantis815 on 2013-10-21
I'm trying to install Virtual Magnifying Glass  [http://magnifier.sourceforge.net/](http://magnifier.sourceforge.net/)    as it's the only program I can find that has a magnifier that follows   the mouse with the actual magnification shown around the cursor  itself. No other linux programs seem to have this feature.    I haven't  installed many programs, but I'm not a complete novice.  I just can't  figure out how to fix these dependencies,so  any help is appreciated.


  After installing, I try to run the program and get
  vmg: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
  When I use ldd to check dependencies, I get.

  ```
chris@Buntzen:/usr/bin$ ldd vmg
  linux-gate.so.1 =>  (0xf76fe000)
libpthread.so.0 => /lib32/libpthread.so.0 (0xf76c8000)
libX11.so.6 => not found
libgdk_pixbuf-2.0.so.0 => not found
libgtk-x11-2.0.so.0 => not found
libgdk-x11-2.0.so.0 => not found
libgobject-2.0.so.0 => not found
libglib-2.0.so.0 => not found
libgthread-2.0.so.0 => not found
libgmodule-2.0.so.0 => not found
libpango-1.0.so.0 => not found
libatk-1.0.so.0 => not found
libcairo.so.2 => not found
libdl.so.2 => /lib32/libdl.so.2 (0xf76c1000)
libc.so.6 => /lib32/libc.so.6 (0xf751a000)
/lib/ld-linux.so.2 (0xf76ff000)
```

  I'm running Ubuntu 12.04, the amd64 version.
  Getting this installed would help me a lot.  Any assistance is appreciated. 
Thanks, 
Chris

---

### Post by mantis815 on 2013-10-22
Problem solved.  I had to install the 32 bit versions of the libraries.

---

