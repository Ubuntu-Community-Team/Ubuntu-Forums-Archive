---
title: "iMule compilation failed"
date: 2008-05-27
forum: General Help
---

### Post by ubu-for on 2008-05-27
I've tried to compile [iMule](http://en.wikipedia.org/wiki/I2P#eDonkey_iMule) for Feisty 32bit and followed the compilation guide, but without success.

```
~/iMule/optimize/src$ ./imule
bash: ./imule: No such file or directory
```

> Compiling iMule
For Linux
Needed tools and libraries

    * Compiler
          o gcc (version >= 4.2.0)
          o gcj (included in gcc) 
    * Libraries
          o wxWidget (version >= 2.8.1) 

Compilation instructions

From iMule topmost directory (for instance iMule-trunk if you followed these instuctions), type :

[B]mkdir optimize
cd optimize
../configure --disable-debug --enable-optimize --enable-irouter
make all

The imule executable should be put in the optimize/src directory (which must have been created by the configure command), along with a libgmp.so library.

Then, to launch iMule :

cd src
./imule[/B]

Of course, if you want to build the debug version, change the configure command :

../configure --enable-debug --disable-optimize --enable-irouter

The --enable-irouter flag is mandatory for versions 1.2.1 and 1.2.2. It is optional for version 1.2.0, 1.2.3 and 1.2.4. It did not even exist in previous versions.

Without the --enable-irouter flag, gcj is not required, and compilation is much faster. But then, you have to replace <your I2P router forlder>/libs/sam.jar by <iMule.tgz>/jars/sam.jar to allow communication between iMule and your I2P router.

Thanks for your help!

---

### Post by Monicker on 2008-05-27
Did configure and make all complete successfully, or were there errors?

---

### Post by ubu-for on 2008-05-27
Yes, I got lots of warnings and some error messages at the end.

Before the compilation I've updated wxWidget to version 2.8.1.1 with Synaptic, but couldn't do the same for gcc 4.1.2.

Do you know how to install the current version of gcc?

---

### Post by andrew.46 on 2008-05-29
Hi,

You should not have to install the compiling tools individually, they are packaged together:

```
$ sudo apt-get install build-essential
```

It seems you need the so-called 'dev' files for wxWidget:

```
$ sudo apt-get install libwxbase2.6-dev libwxbase2.8-dev libwxgtk2.6-dev libwxgtk2.8-dev pythoncard-tools 
```

An easy way to find the names of such files is to use the same method I used to find these files:

```
$ apt-cache search wxWidget | grep dev
```

After installing these files you should be right to compile the program.

   Andrew

---

### Post by ubu-for on 2008-05-31
After the installation of the recommended files, I get an error message as early as I enter the configure code.

```
~/iMule/optimize$ ../configure --disable-debug --enable-optimize --enable-irouter
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcj... no
checking for gcj-3.2... no
checking for gcj-3.1... no
checking for gcj-3.0... no
checking for gcj-2.95... no
checking dependency style of gcj... none
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for bison... no
checking for byacc... no
checking for ranlib... (cached) ranlib
checking for strip... strip
checking for ar... ar
checking for ld... ld
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for zlib >= 1.1.4... yes (version 1.2.3)
checking whether we need the GUI... yes
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.8.1... no (version 2.6.3 is not new enough)
configure: error:
                wxWidgets must be installed on your system but wx-config
                script couldn't be found. Please check that wx-config is
                in path or specified by --with-wx-config=path flag, the
                directory where wxWidgets libraries are installed (returned
                by 'wx-config --libs' command) is in LD_LIBRARY_PATH or
                equivalent variable and wxWidgets version is 2.6.0 or above.
```

---

### Post by andrew.46 on 2008-06-01
Looks like the configure script is picking up the older version:

```
checking for wxWidgets version >= 2.8.1... no (version 2.6.3 is not new enough)
```

Hardy Heron has both versions in the repository make sure you remove the older one and install the 2.8 files including the dev files.

           Andrew

---

### Post by johndoe32102002 on 2010-07-08
You could try to install aMule first, and then install the iMule binaries (*.deb for i386 or amd64).  They are downloadable from echelon.i2p.  This might clear up dependencies errors that are stopping you from installing the iMule binaries in the first place.

---

