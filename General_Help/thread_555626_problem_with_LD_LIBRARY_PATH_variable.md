---
title: "problem with LD_LIBRARY_PATH variable"
date: 2007-09-20
forum: General Help
---

### Post by ohren on 2007-09-20
Hello,

I'm trying to use xerces-c with eclipse, and I've the next error: error while loading shared libraries: libxerces-c.so.28: cannot open shared object file: No such file or directory.
 
The problem is the next: when I export LD_LIBRARY_PATH in .profile the variable is not saved whereas exporting the variable directly in a terminal is well established. I think that's the reason because eclipse doesn't find the library, but I don't Know what's the solution.

Someone can help me?

Thank you

---

### Post by ddrichardson on 2007-09-21
I could be wrong but think .profile is deprecated - does it export from .bashrc or .login?

---

