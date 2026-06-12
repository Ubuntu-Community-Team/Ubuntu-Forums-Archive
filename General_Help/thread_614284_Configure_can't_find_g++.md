---
title: "Configure can't find g++"
date: 2007-11-15
forum: General Help
---

### Post by kkrelove on 2007-11-15
I'm trying to compile a utility that doesn't seem to be available as an Ubuntu package (ksplit). When I do ./configure the C compiler (GCC) is found but then it stops with an error that says "configure: error: no acceptable C++-compiler found in $PATH." I have installed g++ using Synaptic Package Manager and can find it manually in the same directory as GCC (/usr/bin), so the directory must be in $PATH or configure wouldn't find gcc either. When I type $PATH at a command prompt the directory is listed. What could be the problem?

Is there a native Ubuntu or Debian utility that will assemble files broken up with ksplit (they have extensions .000, .001, .002, etc.)?

Thanks for any help.

Karl

---

### Post by taurus on 2007-11-15
How did you install GCC?  If you installed it by hand, you are missing a few things.  You need the build-essential package if you want to build or compile anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by kkrelove on 2007-11-15
Thanks. I think I installed it with Synaptic, but I'll try your suggestion.

Karl

---

### Post by kkrelove on 2007-11-15
Now, it finds g++ but stops and says it can't find libz. What still needs to be installed?

TIA

Karl

---

### Post by taurus on 2007-11-15
If you can post the complete error message, perhaps I could give you a better idea what developing package you need to install.

---

### Post by kkrelove on 2007-11-15
checking for libz... configure: error: not found. Check your installation and look into config.log

The final section of configure.log is:

int main() {
shl_unload()
; return 0; }
configure:4379: checking for extra includes
configure:4410: checking for extra libs
configure:4444: checking for libz
configure:4470: gcc -o conftest -O2     conftest.c   -lz  1>&5
configure:4463:17: error: zlib.h: No such file or directory
configure: In function 'main':
configure:4466: error: 'ZLIB_VERSION' undeclared (first use in this function)
configure:4466: error: (Each undeclared identifier is reported only once
configure:4466: error: for each function it appears in.)
configure: failed program was:
#line 4461 "configure"
#include "confdefs.h"

#include<zlib.h>

int main() {
return (zlibVersion() == ZLIB_VERSION); 
; return 0; }

---

### Post by taurus on 2007-11-15
Maybe it's looking for zlibc.

```
sudo apt-get update
sudo apt-get install zlibc
```

---

