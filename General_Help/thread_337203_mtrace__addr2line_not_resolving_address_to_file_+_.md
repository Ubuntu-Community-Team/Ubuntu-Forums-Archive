---
title: "mtrace / addr2line not resolving address to file + line number"
date: 2007-01-12
forum: General Help
---

### Post by jph4599 on 2007-01-12
I am attempting to use mtrace to do some memory leak detection but am unable to get it to resolve addresses to file names with line numbers.  I have been working at this for at least 2 days now and am out of ideas.  I hope someone at this forum may be able to offer some assistance.

I have created a very simple c++ file to test with:
```
linuxcom-04> cat leak.cc
#include <mcheck.h>
#include <iostream>

using namespace std;

int main(int argc, char *argv[])
{
    mtrace();
    cout << "hello world" << endl;
    char* str = new char[20];
}
```

I have set the environment variable:
```
linuxcom-04> echo $MALLOC_TRACE
leak.out

```

And compiled with debugging:
```
linuxcom-04> g++ -g leak.cc
linuxcom-04> ls
a.out  leak.cc
```

Ran the program once and got the mtrace output file
```
linuxcom-04> ./a.out
hello world

linuxcom-04> ls
a.out  leak.cc  leak.out
```

Ran mtrace with the executable name and the log file
```
linuxcom-04> mtrace a.out leak.out

Memory not freed:
-----------------
   Address     Size     Caller
0x0949a378     0x14  at 0x92b86e

```

and only got the address of the caller.  I believe mtrace uses addr2line so I figured I would attempt using that directly, but it was no help:
```
linuxcom-04> addr2line -e a.out 0x92b86e
??:0
```

linuxcom-04> addr2line --version
GNU addr2line 2.17.50.0.3 20060715

linuxcom-04> mtrace --version
mtrace (GNU libc) 2.3.2

I have tried on both ppc and i386-linux systems with different executables.  I have updated binutils.  I've done a mess of other little things trying to find out what the problem could possibly be.

I really hope someone here will be able to offer some assistance and end my suffering.

Thank you for your time,
-Jesse Harvey

---

