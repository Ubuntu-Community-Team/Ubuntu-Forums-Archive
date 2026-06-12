---
title: "After 14.10 upgrade, cannot link against against pthread using C++11 &lt;thread&gt;"
date: 2015-04-12
forum: General Help
---

### Post by nick186 on 2015-04-12
Hi all, first post, sorry if I'm in the wrong sub forum.

So I recently upgraded my headless server from 14.04 to 14.10 using `sudo do-release-upgrade -d`.  After the upgrade, I had to reinstall boost, but [one of my projects]("https://github.com/nickdesaulniers/cpp11-memcached") that I build with cmake stopped building.

```
&#10140;  build git:(master) cmake ..
-- The C compiler identification is GNU 4.9.2
-- The CXX compiler identification is GNU 4.9.2
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Boost version: 1.55.0
-- Found the following Boost libraries:
--   system
-- Configuring done
-- Generating done
-- Build files have been written to: /home/nick/slack/cpp11-memcached/build
&#10140;  build git:(master) &#10007; make
Scanning dependencies of target main
[ 33%] Building CXX object CMakeFiles/main.dir/hello.cpp.o
[ 66%] Building CXX object CMakeFiles/main.dir/packet.cpp.o
[100%] Building CXX object CMakeFiles/main.dir/key_value_store.cpp.o
Linking CXX executable main
/usr/bin/ld: CMakeFiles/main.dir/hello.cpp.o: undefined reference to symbol 'pthread_create@@GLIBC_2.2.5'
/lib/x86_64-linux-gnu/libpthread.so.0: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
CMakeFiles/main.dir/build.make:136: recipe for target 'main' failed
make[2]: *** [main] Error 1
CMakeFiles/Makefile2:60: recipe for target 'CMakeFiles/main.dir/all' failed
make[1]: *** [CMakeFiles/main.dir/all] Error 2
Makefile:76: recipe for target 'all' failed
make: *** [all] Error 2
```

This would build fine in 14.04 without having to explicitly link against pthread.  I'm not sure what's missing, or if I need to upgrade something?

```
&#10140;  build git:(master) &#10007; cc -v
Using built-in specs.
COLLECT_GCC=cc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.9.2-10ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.9/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.9 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.9 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.9-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu12)
&#10140;  build git:(master) &#10007; cmake --version
cmake version 3.0.2
```

---

### Post by nick186 on 2015-04-12
More info:

```
&#10140;  build git:(master) &#10007; c++ -v
Using built-in specs.
COLLECT_GCC=c++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.9.2-10ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.9/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.9 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.9 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.9-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu12)
&#10140;  build git:(master) &#10007; cat test.cpp
#include <thread>

void bar () {}

int main () {
  std::thread a(bar);
}
&#10140;  build git:(master) &#10007; c++ test.cpp -std=c++11
/tmp/ccS1tEuk.o: In function `std::thread::thread<void (&)()>(void (&)())':
test.cpp:(.text._ZNSt6threadC2IRFvvEIEEEOT_DpOT0_[_ZNSt6threadC5IRFvvEIEEEOT_DpOT0_]+0x2d): undefined reference to `pthread_create'
collect2: error: ld returned 1 exit status
```

---

### Post by nick186 on 2015-04-12
Actually, I may have been a little overzealous with the use of `sudo do-release-upgrade -d`:

```
&#10140;  build git:(master) &#10007; lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
```

---

### Post by nick186 on 2015-04-13
lol wut, not sure why this was required all of a sudden: [https://github.com/nickdesaulniers/cpp11-memcached/commit/4ce7505335c59754033b3c90409be050eb48d134](https://github.com/nickdesaulniers/cpp11-memcached/commit/4ce7505335c59754033b3c90409be050eb48d134)

---

### Post by nick186 on 2015-04-13
Let's see what cmake devs think: [http://public.kitware.com/Bug/view.php?id=15510](http://public.kitware.com/Bug/view.php?id=15510)

---

### Post by nick186 on 2015-04-13
So it looks like libstdc++ (the GNU C++ runtime) requires you to explicitly link against pthreads when using <thread> in C++11.  This would result in a runtime crash(?) up to GCC 4.9, where it could now be caught at link time.  [https://gcc.gnu.org/bugzilla/show_bug.cgi?id=61841](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=61841)

Here's how I patched my code:
[https://github.com/nickdesaulniers/cpp11-memcached/commit/85a45555356e979ec8aac9198d0711dacf1c4fdc](https://github.com/nickdesaulniers/cpp11-memcached/commit/85a45555356e979ec8aac9198d0711dacf1c4fdc)

---

