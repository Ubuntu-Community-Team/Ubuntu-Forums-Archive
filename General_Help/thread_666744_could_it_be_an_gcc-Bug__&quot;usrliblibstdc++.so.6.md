---
title: "could it be an gcc-Bug ?? &quot;/usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found"
date: 2008-01-13
forum: General Help
---

### Post by VAB on 2008-01-13
Long time with no worries using ubuntu but now ....

When trying to install a program (it's a quite technical math program I leave the name out of the discussion, call it "foo")
in a "ubuntu 6.10 Edgy Fit" distribution the following error comes up persistently:

/usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by ..."foo"....)

All other applications work fine and also, curiously enough, the same program runs flawlessly in the older  distribution ("Ubuntu 6.06 LTS  Dapper Drake"). All libraries are there and all essential packages too.
](*,)
If anyone could give me a clue as to what is happening gcc-bug? ubuntu-bug?
and / or how to fix it I would be absolutely grateful!!!

Thanks!

---

### Post by geraldm on 2008-01-14
A google for GLIBXX_3.4.9 shows that a lot of developers have run into that problem, and from the alleged solutions, there does not seem to be any one answer for a solution.  The problem seems to come from mis-matched dependencies of libstdc++.so.6
My guess is that /usr/lib/libstdc++.so.6 at some time required the symbol, and obtaining a libstdc++.so.6 that does not need the symbol would be a solution.  

```

 nm /usr/lib/libstdc++.so.6 | grep GLIBCXX_3.4.9 -

```
results shows (my results come from the gcc-4.2.0 package)
00000000 A GLIBCXX_3.4.9

Gerald

---

### Post by VAB on 2008-01-15
Thanks,
I see the bigger issue with gcc now, more clearly. It is sad but ...

So, is the only solution to link against another older version of gcc 
or one can link only to an istant of libstdc++ which contains GLIBXX_3.4.9?

I wonder how one finds the correct version of either anyway ...


Thanks a again

---

### Post by geraldm on 2008-01-15
I am thinking that the symbol is used to identify compatibility between different libstdc++ versions. 
GLIBCXX_3.4.9 -> gcc-4.2.0
GLIBCXX_3.4.8 -> gcc-4.1.2

In the source gcc TOPDIR/libstdc++v3/src/compatibility.cc it says:
// In the future, GLIBCXX_ABI > 6 should remove all uses of
// _GLIBCXX_*_SYMVER macros in this file.

If gcc-4.2.0 is used, then it is necessary to deal with the symbol.
Older compilers also have some version information for libstdc++ but 3.4.9 does not appear.

From the name of the symbol, it may refer to features in glibc for C++, the underlying C library on the host.

Gerald

---

