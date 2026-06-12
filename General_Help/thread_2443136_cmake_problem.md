---
title: "cmake problem"
date: 2020-05-11
forum: General Help
---

### Post by kbrontox on 2020-05-11
hi every one i dunno if i can ask for help on here but im traying to install a programg named Darling (mac support) and i have this problem i try to find info about how to resolved but no look
 i use  "cmake .." and this happend
> -- Found dsymutil: /usr/bin/llvm-dsymutil-6.0-- Compiler include path detected as /usr/lib/llvm-6.0/lib/clang/6.0.0/include/
-- Found FFMPEG or Libav: /usr/lib/x86_64-linux-gnu/libavcodec.so;/usr/lib/x86_64-linux-gnu/libavformat.so;/usr/lib/x86_64-linux-gnu/libavutil.so, /usr/include/x86_64-linux-gnu
CMake Error at src/external/cocotron/AppKit/CMakeLists.txt:31 (message):
  xkbfile not found




-- Configuring incomplete, errors occurred!
See also "/home/joe/darling/build/CMakeFiles/CMakeOutput.log".

---

### Post by monkeybrain20122 on 2020-05-12
This tells you that the dependency xkbfile is missing. So just install it
```
sudo apt install libxkbfile-dev
```

Ubuntu usually name them "lib" and for compiling stuffs you usually need the -dev package (for header files).

---

### Post by kbrontox on 2020-05-12
thanks alot

---

