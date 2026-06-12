---
title: "Broke my gcc and c std library with mingw"
date: 2015-06-03
forum: General Help
---

### Post by Holotype on 2015-06-03
I'm on Ubuntu 12.04, and I was installing mingw to compile a windows c++ program. I screwed up somewhere, and it now seems easier to just change the code instead. The problem is, now that I am compiling the program foo, I got an error related to _mingw. I tried to remove the headers related to mingw, purge mingw, and reinstall build-essential, binutils, gcc, g++ and others, but it still wants to use _mingw. So, I start removing all traces, and now I get the error:

fatal error: crtdefs.h: No such file or directory

I have also tried rebuilding the clib, but it keeps wanting to use mingw. How do I get around this? How can I rebuild g++ without mingw getting in the way?

Thank you

---

