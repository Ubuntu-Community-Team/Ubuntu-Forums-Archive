---
title: "How to CMake cross compile a package for particular ARM architecture?"
date: 2019-09-08
forum: General Help
---

### Post by jiapei100 on 2019-09-08
Hi, all:

I'm actually trying to use **my own toolchain** generated from [crosstool-NG]("https://github.com/crosstool-ng/crosstool-ng/") to build some packages, for instance, [flann]("https://github.com/mariusmuja/flann"), onto a particular ARM board, here in my case: a raspberry pi 3B. I strictly followed [CMake toolchain documentation]("https://cmake.org/cmake/help/latest/manual/cmake-toolchains.7.html"), however, I obtained the following **ERROR** messages:

```

CMake Error at /usr/share/cmake-3.13/Modules/CMakeTestCCompiler.cmake:52 (message):
   The C compiler

     "....../RPi/bin/arm-rpi-linux-gnueabihf-gcc"

   is not able to compile a simple test program.

   It fails with the following output:

     Change Dir: ....../flann/build/CMakeFiles/CMakeTmp

     Run Build Command:"/usr/bin/make" "cmTC_78471/fast"
     /usr/bin/make -f CMakeFiles/cmTC_78471.dir/build.make CMakeFiles/cmTC_78471.dir/build
     make[1]: Entering directory '....../flann/build/CMakeFiles/CMakeTmp'
     Building C object CMakeFiles/cmTC_78471.dir/testCCompiler.c.o
     ....../RPi/bin/arm-rpi-linux-gnueabihf-gcc --sysroot=....../rootfs    -o
 CMakeFiles/cmTC_78471.dir/testCCompiler.c.o   -c ....../flann/build/CMakeFiles/CMakeTmp/testCCompiler.c
     Linking C executable cmTC_78471
     /usr/bin/cmake -E cmake_link_script CMakeFiles/cmTC_78471.dir/link.txt --verbose=1
     ....../RPi/bin/arm-rpi-linux-gnueabihf-gcc --sysroot=....../rootfs      -rdynamic
 CMakeFiles/cmTC_78471.dir/testCCompiler.c.o  -o cmTC_78471
     ....../RPi/lib/gcc/arm-rpi-linux-gnueabihf/8.3.0/../../../../arm-rpi-linux-gnueabihf/bin/ld: cannot find crt1.o: No such file or directory
     ....../RPi/lib/gcc/arm-rpi-linux-gnueabihf/8.3.0/../../../../arm-rpi-linux-gnueabihf/bin/ld: cannot find crti.o: No such file or directory
     collect2: error: ld returned 1 exit status
     make[1]: *** [CMakeFiles/cmTC_78471.dir/build.make:87: cmTC_78471] Error 1
     make[1]: Leaving directory '....../flann/build/CMakeFiles/CMakeTmp'
     make: *** [Makefile:121: cmTC_78471/fast] Error 2




   CMake will not be able to correctly generate this project.
 Call Stack (most recent call first):
   CMakeLists.txt:24 (project)

```


How to successfully cross compile/build a package with the generated toolchain, without emulating the target system environment?  Particularly, for raspberry pi? 

Can anybody give me a hand?

Cheers
Pei

---

