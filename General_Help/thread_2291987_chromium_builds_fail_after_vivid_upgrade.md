---
title: "chromium builds fail after vivid upgrade"
date: 2015-08-24
forum: General Help
---

### Post by brandonabandon on 2015-08-24
hello, i recently did upgrade from trusty to vivid. since, i am unable to compile chromium for android builds. i quadruple the swapfile amount even, same make error ```
ld.gold: fatal error: /home/brandonabandon/aicp/out/target/product/toroplus/obj/SHARED_LIBRARIES/libwebviewchromium_intermediates/LINKED/libwebviewchromium.so: mmap: failed to allocate 1517458680 bytes for output file: Cannot allocate memory
collect2: error: ld returned 1 exit status
build/core/shared_library_internal.mk:68: recipe for target '/home/brandonabandon/aicp/out/target/product/toroplus/obj/SHARED_LIBRARIES/libwebviewchromium_intermediates/LINKED/libwebviewchromium.so' failed
make: *** [/home/brandonabandon/aicp/out/target/product/toroplus/obj/SHARED_LIBRARIES/libwebviewchromium_intermediates/LINKED/libwebviewchromium.so] Error 1
```
swapfile
```
brandonabandon@beazt:~$ free
             total       used       free     shared    buffers     cached
Mem:       3329552    2564208     765344     107168     149260     780952
-/+ buffers/cache:    1633996    1695556
Swap:     17814520     112092   17702428
```
```
brandonabandon@beazt:~$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    2085884    0    -1
/swapfile                               file        15728636    105024    60
```
previously using a 4g swapfile allowing chromium via trusty. any ideas?

---

