---
title: "missing shared objects"
date: 2008-03-04
forum: General Help
---

### Post by StOoZ on 2008-03-04
what should I do,when im trying to run a program which requires of a file (shared object, I guess) which I dont have? 
I get the following error messege:
> error while loading shared libraries: libncurses.so.4: cannot open shared object file: No such file or directory

thanks in advance

---

### Post by lloyd_b on 2008-03-04
You just need to install the library.  In this case, the package is "libncurses4", so "sudo apt-get install libncurses4" in a terminal window, or use the GUI package manager of your choice (Synaptic, Adept, etc).

Lloyd B.

---

### Post by StOoZ on 2008-03-04
thanks a lot.
and since I want to educate from this scenario , how do I figure out which package is missing in such cases?

---

### Post by lloyd_b on 2008-03-04
> **StOoZ said:**
> thanks a lot.
and since I want to educate from this scenario , how do I figure out which package is missing in such cases?

There are a number of ways to do this, but my preferred solution is to install the "apt-file" package.  Once it is installed, just open up a terminal window, and
```
apt-file search {filename}
```
and it will give you a list of every package that contains a file of that name.

In the case of "libncurses.so.4", here are the results:
```
lloyd@laptop:~$ apt-file search libncurses.so.4
libncurses4: lib/libncurses.so.4
libncurses4: lib/libncurses.so.4
libncurses4: lib/libncurses.so.4
libncurses4: lib/libncurses.so.4.2
libncurses4: lib/libncurses.so.4.2
libncurses4: lib/libncurses.so.4.2
```

Since all of the references point to the same package, the answer is obvious.  In some cases it may not be.  For instance, a given library may come in both a regular and a "debug" version (such packages usually have "-dbg" on the end of the name), and there are 64 bit versions of some libraries (the names usually start with "lib64").  

If the apt-file results are too ambiguous for you to figure it out, then I'd suggest posting those results here and see if somebody else can identify the correct package for your situation.

Lloyd B.

---

