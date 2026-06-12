---
title: "A compiler with support for C++20 language features is required"
date: 2024-01-04
forum: General Help
---

### Post by ujiko on 2024-01-04
Hello,
I'm on Ubuntu 20.04LTS and i have an issue of compiling ;
```
gilles@bbb:~/bitcoin$ ./configure
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a race-free mkdir -p... /usr/bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking whether make supports nested variables... (cached) yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether the compiler supports GNU C++... yes
checking whether g++ accepts -g... yes
checking for g++ option to enable C++11 features... none needed
checking whether make supports the include directive... yes (GNU style)
checking dependency style of g++... gcc3
checking whether g++ supports C++20 features with -std=c++20... no
checking whether g++ supports C++20 features with +std=c++20... no
checking whether g++ supports C++20 features with -h std=c++20... no
configure: error: *** A compiler with support for C++20 language features is required.

```
Should it work on Ubuntu 22?

---

### Post by MAFoElffen on 2024-01-04
<<This should be moved. Not remotely related to any development version.>> 
C++ 20 was supported since GCC8 in Focal. You already have support for that...

RE: [https://gcc.gnu.org/projects/cxx-status.html](https://gcc.gnu.org/projects/cxx-status.html)
> 
C++20 features are available since GCC 8. To enable C++20 support, [COLOR=#ff0000]add the command-line parameter -std=c++20[/COLOR] (use -std=c++2a in GCC 9 and earlier) to your g++ command line. Or, to enable GNU extensions in addition to C++20 features, add -std=gnu++20.

Which your compile error was telling you:
```

checking whether g++ supports C++20 features with -std=c++20... no
checking whether g++ supports C++20 features with +std=c++20... no
checking whether g++ supports C++20 features with -h std=c++20... n

```

---

### Post by slickymaster on 2024-01-05
*Thread moved to **General Help**.*

---

