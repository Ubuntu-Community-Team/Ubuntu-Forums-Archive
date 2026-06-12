---
title: "Pyrit and OpenCL build error"
date: 2014-01-12
forum: General Help
---

### Post by vsandstoe on 2014-01-12
I am trying to install the opencl extension for pyrit. I am using 2 AMD Radeon HD 6870s with the latest fglrx driver from the software center. I have also installed Pyrit though the software center. When I run "pyrit list_cores" it doesn't show the video cards. I have found on several other forum posts many steps to try and nothing has worked so far. I have installed the AMD APP SDK 2.9 from [http://developer.amd.com/tools-and-sdks/heterogeneous-computing/amd-accelerated-parallel-processing-app-sdk/downloads/](http://developer.amd.com/tools-and-sdks/heterogeneous-computing/amd-accelerated-parallel-processing-app-sdk/downloads/). I have followed the instructions on [http://www.pophams.com/blog/pyritonatigpus-ubuntu1104x64](http://www.pophams.com/blog/pyritonatigpus-ubuntu1104x64) to compile only the opencl extention as the pyrit was installed thought the software center. I understand it was an older post so i changed the directories form the stream sdk to the app sdk. 

Here is the terminal output:

> The headers required to build the OpenCL-kernel were not found. Trying to continue anyway...svn: E155007: '/home/vincent/cpyrit-opencl-0.4.0' is not a working copy
running build
running build_ext
Building modules...
building 'cpyrit._cpyrit_opencl' extension
creating build
creating build/temp.linux-x86_64-2.7
x86_64-linux-gnu-gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/opt/AMDAPP/include/ -I/usr/include/python2.7 -c _cpyrit_opencl.c -o build/temp.linux-x86_64-2.7/_cpyrit_opencl.o -Wall -fno-strict-aliasing -DVERSION="0.4.0"
_cpyrit_opencl.c:47:26: fatal error: openssl/hmac.h: No such file or directory
 #include <openssl/hmac.h>
                          ^
compilation terminated.
error: command 'x86_64-linux-gnu-gcc' failed with exit status 1




Any help would be greatly appriciated!

---

