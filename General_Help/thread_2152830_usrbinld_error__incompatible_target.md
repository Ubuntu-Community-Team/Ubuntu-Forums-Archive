---
title: "/usr/bin/ld: error : incompatible target"
date: 2013-06-09
forum: General Help
---

### Post by fkazemi on 2013-06-09
hi
I want install newest version of gpgpusim v3 on unbuntu 10.04. I install all package like gcc,zlib,g++,opencl, Cuda sdk and toolkit. 
But when i make gpgpusim i recieved this error 
```
/usr/bin/ld: error: /root/Documents/source/gpgpu-sim/v3.x/src/gpuwattch//obj_opt/router.o: incompatible target/usr/bin/ld: error: /root/Documents/source/gpgpu-sim/v3.x/src/gpuwattch//obj_opt/sharedcache.o: incompatible target
/usr/bin/ld: error: /root/Documents/source/gpgpu-sim/v3.x/src/gpuwattch//obj_opt/subarray.o: incompatible target
/usr/bin/ld: error: /root/Documents/source/gpgpu-sim/v3.x/src/gpuwattch//obj_opt/technology.o: incompatible target
/usr/bin/ld: error: /root/Documents/source/gpgpu-sim/v3.x/src/gpuwattch//obj_opt/uca.o: incompatible target
/usr/bin/ld: error: /root/Documents/source/gpgpu-sim/v3.x/src/gpuwattch//obj_opt/wire.o: incompatible target
/usr/bin/ld: error: /root/Documents/source/gpgpu-sim/v3.x/src/gpuwattch//obj_opt/xmlParser.o: incompatible target
collect2: ld returned 1 exit status
make: *** [lib/2030/release/libcudart.so] Error 1

``` 
what should i do with this error?
any suggestion ?
thanks

---

### Post by mcellius on 2013-06-09
Just to try to help a tiny bit: You've posted your question in a section (Ubuntu+1) that deals with testing the version of Ubuntu that is currently in development and is scheduled to be released in a few months.  The people here are good and helpful, but you'll be much more likely to get the help you need if you post your question in a section that handles questions about versions that have already been released.

---

### Post by Iowan on 2013-06-09
Moved to General Help.

---

