---
title: "Need help with cross compiling of openssl for arm-unknown-linux-gnueabi toolchain ?!"
date: 2019-04-12
forum: General Help
---

### Post by fairbird on 2019-04-12
I'm using ubuntu 18.10 and need to compiling of openssl for arm-unknown-linux-gnueab to counting build my ncam
[https://github.com/javilonas/NCam/tree/master/cross/arm-unknown-linux-gnueabi](https://github.com/javilonas/NCam/tree/master/cross/arm-unknown-linux-gnueabi)

Because If got this error before enable openssl when trying to compile emu with enable openssl as log shown
```
CONF build/mipsel-tuxbox-linux-gnu/config.cLINK ncam.mips.debug
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:699: undefined reference to `RSA_private_decrypt'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:699: undefined reference to `RSA_private_decrypt'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:838: undefined reference to `PEM_read_RSAPrivateKey'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:838: undefined reference to `PEM_read_RSAPrivateKey'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:863: undefined reference to `i2d_RSA_PUBKEY'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:863: undefined reference to `i2d_RSA_PUBKEY'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:872: undefined reference to `EVP_MD_CTX_create'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:872: undefined reference to `EVP_MD_CTX_create'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:878: undefined reference to `EVP_sha256'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:878: undefined reference to `EVP_sha256'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:878: undefined reference to `EVP_DigestInit_ex'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:878: undefined reference to `EVP_DigestInit_ex'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:879: undefined reference to `EVP_DigestUpdate'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:879: undefined reference to `EVP_DigestUpdate'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:880: undefined reference to `EVP_DigestFinal_ex'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:880: undefined reference to `EVP_DigestFinal_ex'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:881: undefined reference to `EVP_MD_CTX_destroy'
build/mipsel-tuxbox-linux-gnu/module-emulator-biss.o:/home/raed/NCam/module-emulator-biss.c:881: undefined reference to `EVP_MD_CTX_destroy'

```
and after enable openssl I have got this error
```
LINK    ncam.cortexa9hf-vfp-neon.debug/home/raed/NCam/cross/arm-unknown-linux-gnueabi/bin/../lib/gcc/arm-unknown-linux-gnueabi/4.7.3/../../../../arm-unknown-linux-gnueabi/bin/ld: cannot find -lssl
/home/raed/NCam/cross/arm-unknown-linux-gnueabi/bin/../lib/gcc/arm-unknown-linux-gnueabi/4.7.3/../../../../arm-unknown-linux-gnueabi/bin/ld: cannot find -lcrypto
```
So I need to make cross compiling of openssl for arm-unknown-linux-gnueabi toolchain ..
I have download
```
sudo apt-get install libc6-armel-cross libc6-dev-armel-cross binutils-arm-linux-gnueabi libncurses5-dev
sudo apt-get install gcc-arm-linux-gnueabihf g++-arm-linux-gnueabihf
```
and clone openssl git
```
git clone https://github.com/openssl/openssl.git
```
so The question is what version gcc should I compile with openssl ?!Is should be this
```
make CC=arm-linux-gnueabihf-gcc-8
```
or this
```
make CC=/home/raed/NCam/cross/arm-unknown-linux-gnueabi/bin/arm-unknown-linux-gnueabi-gcc-4.7.3
```

I have useing this steps
```
git clone https://github.com/openssl/openssl.git
cd '/home/raed/openssl'
./Configure linux-armv4 --prefix=/home/raed/openssl --openssldir=/home/raed/openssl shared
make CC=/home/raed/NCam/cross/arm-unknown-linux-gnueabi/bin/arm-unknown-linux-gnueabi-gcc-4.7.3
make install  
```
Is it correct ?!
Because I have got this output
```
make[1]: Leaving directory '/home/raed/openssl'
raed@fairbird:~/openssl$ make install
make depend && make _build_libs
make[1]: Entering directory '/home/raed/openssl'
make[1]: Leaving directory '/home/raed/openssl'
make[1]: Entering directory '/home/raed/openssl'
make[1]: Nothing to be done for '_build_libs'.
make[1]: Leaving directory '/home/raed/openssl'
created directory `/home/raed/openssl/lib'
*** Installing runtime libraries
install libcrypto.so.3 -> /home/raed/openssl/lib/libcrypto.so.3
install libssl.so.3 -> /home/raed/openssl/lib/libssl.so.3
*** Installing development files
install ./include/openssl/aes.h -> /home/raed/openssl/include/openssl/aes.h
cp: './include/openssl/aes.h' and '/home/raed/openssl/include/openssl/aes.h' are the same file
make: *** [Makefile:316: install_dev] Error 1
```

Thank you

---

### Post by fairbird on 2019-04-12
Solved ..

---

### Post by fairbird on 2019-04-15
I have one more issue ?!
I need to know correct Configure to (aarch64) ?!
I have try those commands to Configure but all binary files doesn't work I got this error
```
-sh: /usr/bin/ncam: cannot execute binary file: Exec format error
```
```
./Configure linux-generic32 --prefix=$TOOLCHAIN/aarch64-linux-gnu/ shared no-async 
```
and
```
./Configure linux-generic64 --prefix=$TOOLCHAIN/aarch64-linux-gnu/ shared no-async

```
and
```
./Configure linux-aarch64 --prefix=$TOOLCHAIN/aarch64-linux-gnu/ shared no-async
```
But I got same error ..

And here are list of Configure tp openssl
```
raed@fairbird:~/openssl-1.0.2r$ ./Configure LISTBC-32
BS2000-OSD
BSD-generic32
BSD-generic64
BSD-ia64
BSD-sparc64
BSD-sparcv8
BSD-x86
BSD-x86-elf
BSD-x86_64
Cygwin
Cygwin-x86_64
DJGPP
MPE/iX-gcc
OS2-EMX
OS390-Unix
QNX6
QNX6-i386
ReliantUNIX
SINIX
SINIX-N
UWIN
VC-CE
VC-WIN32
VC-WIN64A
VC-WIN64I
aix-cc
aix-gcc
aix3-cc
aix64-cc
aix64-gcc
android
android-armv7
android-mips
android-x86
aux3-gcc
beos-x86-bone
beos-x86-r5
bsdi-elf-gcc
cc
cray-j90
cray-t3e
darwin-i386-cc
darwin-ppc-cc
darwin64-ppc-cc
darwin64-x86_64-cc
debug
debug-BSD-x86-elf
debug-VC-WIN32
debug-VC-WIN64A
debug-VC-WIN64I
debug-ben
debug-ben-darwin64
debug-ben-debug
debug-ben-debug-64
debug-ben-debug-64-clang
debug-ben-macos
debug-ben-macos-gcc46
debug-ben-no-opt
debug-ben-openbsd
debug-ben-openbsd-debug
debug-ben-strict
debug-bodo
debug-darwin-i386-cc
debug-darwin-ppc-cc
debug-darwin64-x86_64-cc
debug-geoff32
debug-geoff64
debug-levitte-linux-elf
debug-levitte-linux-elf-extreme
debug-levitte-linux-noasm
debug-levitte-linux-noasm-extreme
debug-linux-elf
debug-linux-elf-noefence
debug-linux-generic32
debug-linux-generic64
debug-linux-ia32-aes
debug-linux-pentium
debug-linux-ppro
debug-linux-x86_64
debug-linux-x86_64-clang
debug-rse
debug-solaris-sparcv8-cc
debug-solaris-sparcv8-gcc
debug-solaris-sparcv9-cc
debug-solaris-sparcv9-gcc
debug-steve-opt
debug-steve32
debug-steve64
debug-vos-gcc
dgux-R3-gcc
dgux-R4-gcc
dgux-R4-x86-gcc
dist
gcc
hpux-cc
hpux-gcc
hpux-ia64-cc
hpux-ia64-gcc
hpux-parisc-cc
hpux-parisc-cc-o4
hpux-parisc-gcc
hpux-parisc1_1-cc
hpux-parisc1_1-gcc
hpux-parisc2-cc
hpux-parisc2-gcc
hpux64-ia64-cc
hpux64-ia64-gcc
hpux64-parisc2-cc
hpux64-parisc2-gcc
hurd-x86
iphoneos-cross
irix-cc
irix-gcc
irix-mips3-cc
irix-mips3-gcc
irix64-mips4-cc
irix64-mips4-gcc
linux-aarch64
linux-alpha+bwx-ccc
linux-alpha+bwx-gcc
linux-alpha-ccc
linux-alpha-gcc
linux-aout
linux-armv4
linux-elf
linux-generic32
linux-generic64
linux-ia32-icc
linux-ia64
linux-ia64-icc
linux-mips32
linux-mips64
linux-ppc
linux-ppc64
linux-ppc64le
linux-sparcv8
linux-sparcv9
linux-x32
linux-x86_64
linux-x86_64-clang
linux-x86_64-icc
linux32-s390x
linux64-mips64
linux64-s390x
linux64-sparcv9
mingw
mingw64
ncr-scde
netware-clib
netware-clib-bsdsock
netware-clib-bsdsock-gcc
netware-clib-gcc
netware-libc
netware-libc-bsdsock
netware-libc-bsdsock-gcc
netware-libc-gcc
newsos4-gcc
nextstep
nextstep3.3
osf1-alpha-cc
osf1-alpha-gcc
purify
qnx4
rhapsody-ppc-cc
sco5-cc
sco5-gcc
solaris-sparcv7-cc
solaris-sparcv7-gcc
solaris-sparcv8-cc
solaris-sparcv8-gcc
solaris-sparcv9-cc
solaris-sparcv9-gcc
solaris-x86-cc
solaris-x86-gcc
solaris64-sparcv9-cc
solaris64-sparcv9-gcc
solaris64-x86_64-cc
solaris64-x86_64-gcc
sunos-gcc
tandem-c89
tru64-alpha-cc
uClinux-dist
uClinux-dist64
ultrix-cc
ultrix-gcc
unixware-2.0
unixware-2.1
unixware-7
unixware-7-gcc
vos-gcc
vxworks-mips
vxworks-ppc405
vxworks-ppc60x
vxworks-ppc750
vxworks-ppc750-debug
vxworks-ppc860
vxworks-ppcgen
vxworks-simlinux

```
And the version of cross gcc that I want to compile openssl inside it is (gcc-5.5_aarch64-linux-gnu)

---

