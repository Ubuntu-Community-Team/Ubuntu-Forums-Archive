---
title: "Error when creating a static executable"
date: 2008-04-02
forum: General Help
---

### Post by drthi1 on 2008-04-02
Hi,

I'm trying to create a static executable in c++ using g++ (version 4.1.3). I compile using the following command:

g++ test.cc -o test.exe -static -Wl,--whole-archive

I use -Wl,--whole-archive so that I can run the executable on different versions of linux. I get a large number of errors and I'm not sure how to fix them. They start like:

/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libc.a(dso_handle.o).rodata+0x0): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.1.3/crtbeginT.o.data+0x0): first defined here
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libc.a(s_isinf.o): In function `isinf':
(.text+0x0): multiple definition of `__isinf'

...

Any tips would be appreciated.
drthi1 is online now Report Post   	Edit/Delete Message

---

