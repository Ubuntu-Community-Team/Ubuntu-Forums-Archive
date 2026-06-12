---
title: "Swift 5.4 on Focal throws an Illegal Instructions notice and does a Core Dump"
date: 2021-06-10
forum: General Help
---

### Post by Gvarelov on 2021-06-10
Hi,
Eager to try Swift on a non-Apple hardware, I tried to install and use Swift on my Ubuntu machine. Followed instructions given on swift.org website regarding installation on Linux to the dot, no errors reported until I actually try to use swift by issuing the "swift" command. I get the following slew of error messages:
```
PLEASE submit a bug report to https://bugs.llvm.org/ and include the crash backtrace.
Stack dump:
0.    Program arguments: ./swift 
1.    Swift version 5.4.1 (swift-5.4.1-RELEASE)
./swift[0x55f4f64]
./swift[0x55f2b5e]
./swift[0x55f5145]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x153c0)[0x7fa8f28133c0]
./swift[0x1a924e9]
./swift[0x1a8c4ff]
./swift[0x49d743]
./swift[0x49cb51]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x7fa8f229c0b3]
./swift[0x49c66e]
Illegal instruction (core dumped)

```

Had anyone else encountered anything similar? My Ubuntu version is 20.04, Swift version is 5.4.1 on an AMD old laptop.

---

