---
title: "gdl install problems"
date: 2007-06-16
forum: General Help
---

### Post by hamburglar6 on 2007-06-16
I'm trying to install the gnu data language compiler (gdl) on my machine using ./configure then make.  Here is the output I get when I use ./configure:

> 
kevin@kevin2:~/gdl/gdl-0.9pre4$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for 64-bit OS... "no"
checking for initscr in -lncurses... yes
checking for stifle_history in -lreadline... yes
checking for gsl_block_alloc in -lgsl... yes
checking for cblas_drot in -lgslcblas... yes
checking for plsexit in -lplplotcxxd... yes
checking for GetMagickVersion in -lMagick... yes
checking for nc_open in -lnetcdf... yes
checking for Hopen in -ldf... yes
checking for SDstart in -lmfhdf... yes
checking for H5Fopen in -lhdf5... yes
FFTW lib not explicitely enabled. Using GSL version for FFT.
LIBPROJ4 lib not explicitely enabled. Map projection routines not supported.
Automatic determination of python version.
checking for Py_Initialize in -lpython2.5... yes
System is: i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/antlr/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands


and here is the output make gives:
> 
kevin@kevin2:~/gdl/gdl-0.9pre4$ make
 cd . && /bin/bash /home/kevin/gdl/gdl-0.9pre4/missing --run automake-1.9 --gnu 
src/Makefile.am:57: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:57: 
src/Makefile.am:57: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:57: to `configure.in' and run `aclocal' and `autoconf' again.
src/antlr/Makefile.am:6: library used but `RANLIB' is undefined
src/antlr/Makefile.am:6: 
src/antlr/Makefile.am:6: The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/antlr/Makefile.am:6: to `configure.in' and run `autoconf' again.
src/antlr/Makefile.am:15: Libtool library used but `LIBTOOL' is undefined
src/antlr/Makefile.am:15: 
src/antlr/Makefile.am:15: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/antlr/Makefile.am:15: to `configure.in' and run `aclocal' and `autoconf' again.
make: *** [Makefile.in] Error 1


Does anybody know what I'm doing wrong?

---

### Post by PaulFr on 2007-06-16
Maybe you do not have libtool installed. Check you have libtool installed using **aptitude show libtool**. If not installed, install that using **sudo aptitude install libtool**.

Then run **aclocal**, **autoconf** and **automake** in that order. Then run **./configure** and **make** as before (see [http://en.wikipedia.org/wiki/Autoconf](http://en.wikipedia.org/wiki/Autoconf) for details on the flow).

---

### Post by hamburglar6 on 2007-06-16
Thanks for responding so quickly!

You were right that I didn't have libtool installed, but it looks like I have more problems than just that- here is the output for ./configure after following the steps you gave:

> 
kevin@kevin2:~/gdl/gdl-0.9pre4$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for 64-bit OS... "no"
checking for initscr in -lncurses... yes
checking for stifle_history in -lreadline... yes
checking for gsl_block_alloc in -lgsl... yes
checking for cblas_drot in -lgslcblas... yes
checking for plsexit in -lplplotcxxd... yes
checking for GetMagickVersion in -lMagick... yes
checking for nc_open in -lnetcdf... yes
checking for Hopen in -ldf... yes
checking for SDstart in -lmfhdf... yes
checking for H5Fopen in -lhdf5... yes
FFTW lib not explicitely enabled. Using GSL version for FFT.
LIBPROJ4 lib not explicitely enabled. Map projection routines not supported.
Automatic determination of python version.
checking for Py_Initialize in -lpython2.5... yes
System is: i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/antlr/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands






and make:

> 
 kevin@kevin2:~/gdl/gdl-0.9pre4$ make
cd . && /bin/bash /home/kevin/gdl/gdl-0.9pre4/missing --run autoheader
rm -f stamp-h1
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
make  all-recursive
make[1]: Entering directory `/home/kevin/gdl/gdl-0.9pre4'
Making all in src
make[2]: Entering directory `/home/kevin/gdl/gdl-0.9pre4/src'
Making all in antlr
make[3]: Entering directory `/home/kevin/gdl/gdl-0.9pre4/src/antlr'
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-ANTLRUtil.o -MD -MP -MF .deps/libantlr_a-ANTLRUtil.Tpo -c -o libantlr_a-ANTLRUtil.o `test -f 'ANTLRUtil.cpp' || echo './'`ANTLRUtil.cpp
mv -f .deps/libantlr_a-ANTLRUtil.Tpo .deps/libantlr_a-ANTLRUtil.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-ASTFactory.o -MD -MP -MF .deps/libantlr_a-ASTFactory.Tpo -c -o libantlr_a-ASTFactory.o `test -f 'ASTFactory.cpp' || echo './'`ASTFactory.cpp
mv -f .deps/libantlr_a-ASTFactory.Tpo .deps/libantlr_a-ASTFactory.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-ASTNULLType.o -MD -MP -MF .deps/libantlr_a-ASTNULLType.Tpo -c -o libantlr_a-ASTNULLType.o `test -f 'ASTNULLType.cpp' || echo './'`ASTNULLType.cpp
mv -f .deps/libantlr_a-ASTNULLType.Tpo .deps/libantlr_a-ASTNULLType.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-ASTRefCount.o -MD -MP -MF .deps/libantlr_a-ASTRefCount.Tpo -c -o libantlr_a-ASTRefCount.o `test -f 'ASTRefCount.cpp' || echo './'`ASTRefCount.cpp
mv -f .deps/libantlr_a-ASTRefCount.Tpo .deps/libantlr_a-ASTRefCount.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-BaseAST.o -MD -MP -MF .deps/libantlr_a-BaseAST.Tpo -c -o libantlr_a-BaseAST.o `test -f 'BaseAST.cpp' || echo './'`BaseAST.cpp
mv -f .deps/libantlr_a-BaseAST.Tpo .deps/libantlr_a-BaseAST.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-BitSet.o -MD -MP -MF .deps/libantlr_a-BitSet.Tpo -c -o libantlr_a-BitSet.o `test -f 'BitSet.cpp' || echo './'`BitSet.cpp
mv -f .deps/libantlr_a-BitSet.Tpo .deps/libantlr_a-BitSet.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-CharBuffer.o -MD -MP -MF .deps/libantlr_a-CharBuffer.Tpo -c -o libantlr_a-CharBuffer.o `test -f 'CharBuffer.cpp' || echo './'`CharBuffer.cpp
mv -f .deps/libantlr_a-CharBuffer.Tpo .deps/libantlr_a-CharBuffer.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-CharScanner.o -MD -MP -MF .deps/libantlr_a-CharScanner.Tpo -c -o libantlr_a-CharScanner.o `test -f 'CharScanner.cpp' || echo './'`CharScanner.cpp
mv -f .deps/libantlr_a-CharScanner.Tpo .deps/libantlr_a-CharScanner.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-CommonAST.o -MD -MP -MF .deps/libantlr_a-CommonAST.Tpo -c -o libantlr_a-CommonAST.o `test -f 'CommonAST.cpp' || echo './'`CommonAST.cpp
mv -f .deps/libantlr_a-CommonAST.Tpo .deps/libantlr_a-CommonAST.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-CommonASTWithHiddenTokens.o -MD -MP -MF .deps/libantlr_a-CommonASTWithHiddenTokens.Tpo -c -o libantlr_a-CommonASTWithHiddenTokens.o `test -f 'CommonASTWithHiddenTokens.cpp' || echo './'`CommonASTWithHiddenTokens.cpp
mv -f .deps/libantlr_a-CommonASTWithHiddenTokens.Tpo .deps/libantlr_a-CommonASTWithHiddenTokens.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-CommonHiddenStreamToken.o -MD -MP -MF .deps/libantlr_a-CommonHiddenStreamToken.Tpo -c -o libantlr_a-CommonHiddenStreamToken.o `test -f 'CommonHiddenStreamToken.cpp' || echo './'`CommonHiddenStreamToken.cpp
mv -f .deps/libantlr_a-CommonHiddenStreamToken.Tpo .deps/libantlr_a-CommonHiddenStreamToken.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-CommonToken.o -MD -MP -MF .deps/libantlr_a-CommonToken.Tpo -c -o libantlr_a-CommonToken.o `test -f 'CommonToken.cpp' || echo './'`CommonToken.cpp
mv -f .deps/libantlr_a-CommonToken.Tpo .deps/libantlr_a-CommonToken.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-InputBuffer.o -MD -MP -MF .deps/libantlr_a-InputBuffer.Tpo -c -o libantlr_a-InputBuffer.o `test -f 'InputBuffer.cpp' || echo './'`InputBuffer.cpp
mv -f .deps/libantlr_a-InputBuffer.Tpo .deps/libantlr_a-InputBuffer.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-LLkParser.o -MD -MP -MF .deps/libantlr_a-LLkParser.Tpo -c -o libantlr_a-LLkParser.o `test -f 'LLkParser.cpp' || echo './'`LLkParser.cpp
mv -f .deps/libantlr_a-LLkParser.Tpo .deps/libantlr_a-LLkParser.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-MismatchedCharException.o -MD -MP -MF .deps/libantlr_a-MismatchedCharException.Tpo -c -o libantlr_a-MismatchedCharException.o `test -f 'MismatchedCharException.cpp' || echo './'`MismatchedCharException.cpp
mv -f .deps/libantlr_a-MismatchedCharException.Tpo .deps/libantlr_a-MismatchedCharException.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-MismatchedTokenException.o -MD -MP -MF .deps/libantlr_a-MismatchedTokenException.Tpo -c -o libantlr_a-MismatchedTokenException.o `test -f 'MismatchedTokenException.cpp' || echo './'`MismatchedTokenException.cpp
mv -f .deps/libantlr_a-MismatchedTokenException.Tpo .deps/libantlr_a-MismatchedTokenException.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-NoViableAltException.o -MD -MP -MF .deps/libantlr_a-NoViableAltException.Tpo -c -o libantlr_a-NoViableAltException.o `test -f 'NoViableAltException.cpp' || echo './'`NoViableAltException.cpp
mv -f .deps/libantlr_a-NoViableAltException.Tpo .deps/libantlr_a-NoViableAltException.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-NoViableAltForCharException.o -MD -MP -MF .deps/libantlr_a-NoViableAltForCharException.Tpo -c -o libantlr_a-NoViableAltForCharException.o `test -f 'NoViableAltForCharException.cpp' || echo './'`NoViableAltForCharException.cpp
mv -f .deps/libantlr_a-NoViableAltForCharException.Tpo .deps/libantlr_a-NoViableAltForCharException.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-Parser.o -MD -MP -MF .deps/libantlr_a-Parser.Tpo -c -o libantlr_a-Parser.o `test -f 'Parser.cpp' || echo './'`Parser.cpp
mv -f .deps/libantlr_a-Parser.Tpo .deps/libantlr_a-Parser.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-RecognitionException.o -MD -MP -MF .deps/libantlr_a-RecognitionException.Tpo -c -o libantlr_a-RecognitionException.o `test -f 'RecognitionException.cpp' || echo './'`RecognitionException.cpp
mv -f .deps/libantlr_a-RecognitionException.Tpo .deps/libantlr_a-RecognitionException.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-String.o -MD -MP -MF .deps/libantlr_a-String.Tpo -c -o libantlr_a-String.o `test -f 'String.cpp' || echo './'`String.cpp
mv -f .deps/libantlr_a-String.Tpo .deps/libantlr_a-String.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-TokenBuffer.o -MD -MP -MF .deps/libantlr_a-TokenBuffer.Tpo -c -o libantlr_a-TokenBuffer.o `test -f 'TokenBuffer.cpp' || echo './'`TokenBuffer.cpp
mv -f .deps/libantlr_a-TokenBuffer.Tpo .deps/libantlr_a-TokenBuffer.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-Token.o -MD -MP -MF .deps/libantlr_a-Token.Tpo -c -o libantlr_a-Token.o `test -f 'Token.cpp' || echo './'`Token.cpp
mv -f .deps/libantlr_a-Token.Tpo .deps/libantlr_a-Token.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-TokenStreamBasicFilter.o -MD -MP -MF .deps/libantlr_a-TokenStreamBasicFilter.Tpo -c -o libantlr_a-TokenStreamBasicFilter.o `test -f 'TokenStreamBasicFilter.cpp' || echo './'`TokenStreamBasicFilter.cpp
mv -f .deps/libantlr_a-TokenStreamBasicFilter.Tpo .deps/libantlr_a-TokenStreamBasicFilter.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-TokenStreamHiddenTokenFilter.o -MD -MP -MF .deps/libantlr_a-TokenStreamHiddenTokenFilter.Tpo -c -o libantlr_a-TokenStreamHiddenTokenFilter.o `test -f 'TokenStreamHiddenTokenFilter.cpp' || echo './'`TokenStreamHiddenTokenFilter.cpp
mv -f .deps/libantlr_a-TokenStreamHiddenTokenFilter.Tpo .deps/libantlr_a-TokenStreamHiddenTokenFilter.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-TokenStreamSelector.o -MD -MP -MF .deps/libantlr_a-TokenStreamSelector.Tpo -c -o libantlr_a-TokenStreamSelector.o `test -f 'TokenStreamSelector.cpp' || echo './'`TokenStreamSelector.cpp
mv -f .deps/libantlr_a-TokenStreamSelector.Tpo .deps/libantlr_a-TokenStreamSelector.Po
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../src     -g -O2 -MT libantlr_a-TreeParser.o -MD -MP -MF .deps/libantlr_a-TreeParser.Tpo -c -o libantlr_a-TreeParser.o `test -f 'TreeParser.cpp' || echo './'`TreeParser.cpp
mv -f .deps/libantlr_a-TreeParser.Tpo .deps/libantlr_a-TreeParser.Po
rm -f libantlr.a
ar cru libantlr.a libantlr_a-ANTLRUtil.o libantlr_a-ASTFactory.o libantlr_a-ASTNULLType.o libantlr_a-ASTRefCount.o libantlr_a-BaseAST.o libantlr_a-BitSet.o libantlr_a-CharBuffer.o libantlr_a-CharScanner.o libantlr_a-CommonAST.o libantlr_a-CommonASTWithHiddenTokens.o libantlr_a-CommonHiddenStreamToken.o libantlr_a-CommonToken.o libantlr_a-InputBuffer.o libantlr_a-LLkParser.o libantlr_a-MismatchedCharException.o libantlr_a-MismatchedTokenException.o libantlr_a-NoViableAltException.o libantlr_a-NoViableAltForCharException.o libantlr_a-Parser.o libantlr_a-RecognitionException.o libantlr_a-String.o libantlr_a-TokenBuffer.o libantlr_a-Token.o libantlr_a-TokenStreamBasicFilter.o libantlr_a-TokenStreamHiddenTokenFilter.o libantlr_a-TokenStreamSelector.o libantlr_a-TreeParser.o 
ranlib libantlr.a
make[3]: Leaving directory `/home/kevin/gdl/gdl-0.9pre4/src/antlr'
make[3]: Entering directory `/home/kevin/gdl/gdl-0.9pre4/src'
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-assocdata.o -MD -MP -MF .deps/gdl-assocdata.Tpo -c -o gdl-assocdata.o `test -f 'assocdata.cpp' || echo './'`assocdata.cpp
mv -f .deps/gdl-assocdata.Tpo .deps/gdl-assocdata.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-basic_fun_cl.o -MD -MP -MF .deps/gdl-basic_fun_cl.Tpo -c -o gdl-basic_fun_cl.o `test -f 'basic_fun_cl.cpp' || echo './'`basic_fun_cl.cpp
mv -f .deps/gdl-basic_fun_cl.Tpo .deps/gdl-basic_fun_cl.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-basic_fun.o -MD -MP -MF .deps/gdl-basic_fun.Tpo -c -o gdl-basic_fun.o `test -f 'basic_fun.cpp' || echo './'`basic_fun.cpp
mv -f .deps/gdl-basic_fun.Tpo .deps/gdl-basic_fun.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-basic_fun_jmg.o -MD -MP -MF .deps/gdl-basic_fun_jmg.Tpo -c -o gdl-basic_fun_jmg.o `test -f 'basic_fun_jmg.cpp' || echo './'`basic_fun_jmg.cpp
mv -f .deps/gdl-basic_fun_jmg.Tpo .deps/gdl-basic_fun_jmg.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-basic_op.o -MD -MP -MF .deps/gdl-basic_op.Tpo -c -o gdl-basic_op.o `test -f 'basic_op.cpp' || echo './'`basic_op.cpp
mv -f .deps/gdl-basic_op.Tpo .deps/gdl-basic_op.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-basic_pro.o -MD -MP -MF .deps/gdl-basic_pro.Tpo -c -o gdl-basic_pro.o `test -f 'basic_pro.cpp' || echo './'`basic_pro.cpp
mv -f .deps/gdl-basic_pro.Tpo .deps/gdl-basic_pro.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-basic_pro_jmg.o -MD -MP -MF .deps/gdl-basic_pro_jmg.Tpo -c -o gdl-basic_pro_jmg.o `test -f 'basic_pro_jmg.cpp' || echo './'`basic_pro_jmg.cpp
mv -f .deps/gdl-basic_pro_jmg.Tpo .deps/gdl-basic_pro_jmg.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-CFMTLexer.o -MD -MP -MF .deps/gdl-CFMTLexer.Tpo -c -o gdl-CFMTLexer.o `test -f 'CFMTLexer.cpp' || echo './'`CFMTLexer.cpp
mv -f .deps/gdl-CFMTLexer.Tpo .deps/gdl-CFMTLexer.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-color.o -MD -MP -MF .deps/gdl-color.Tpo -c -o gdl-color.o `test -f 'color.cpp' || echo './'`color.cpp
mv -f .deps/gdl-color.Tpo .deps/gdl-color.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-convert2.o -MD -MP -MF .deps/gdl-convert2.Tpo -c -o gdl-convert2.o `test -f 'convert2.cpp' || echo './'`convert2.cpp
mv -f .deps/gdl-convert2.Tpo .deps/gdl-convert2.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-datatypes.o -MD -MP -MF .deps/gdl-datatypes.Tpo -c -o gdl-datatypes.o `test -f 'datatypes.cpp' || echo './'`datatypes.cpp
datatypes.cpp:21:34: error: numarray/libnumarray.h: No such file or directory
topython.cpp:61: error: &#8216;NumarrayType&#8217; does not name a type
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython()&#8217;:
topython.cpp:90: error: &#8216;NumarrayType&#8217; does not name a type
topython.cpp:91: error: &#8216;item_type&#8217; was not declared in this scope
topython.cpp:91: error: &#8216;tAny&#8217; was not declared in this scope
topython.cpp:95: error: &#8216;maybelong&#8217; was not declared in this scope
topython.cpp:95: error: expected `;' before &#8216;dimArr&#8217;
topython.cpp:96: error: &#8216;dimArr&#8217; was not declared in this scope
topython.cpp:99: error: &#8216;item_type&#8217; was not declared in this scope
topython.cpp:99: error: &#8216;dimArr&#8217; was not declared in this scope
gdlpython.cpp: In function &#8216;void PythonInit()&#8217;:
gdlpython.cpp:47: error: &#8216;import_libnumarray&#8217; was not declared in this scope
gdlpython.cpp: At global scope:
gdlpython.cpp:58: error: &#8216;PyArrayObject&#8217; has not been declared
gdlpython.cpp: In function &#8216;T* NewFromPyArrayObject(const dimension&, int*)&#8217;:
gdlpython.cpp:63: error: there are no arguments to &#8216;NA_OFFSETDATA&#8217; that depend on a template parameter, so a declaration of &#8216;NA_OFFSETDATA&#8217; must be available
gdlpython.cpp:63: error: (if you use &#8216;-fpermissive&#8217;, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
gdlpython.cpp:65: error: request for member &#8216;ob_refcnt&#8217; in &#8216;array->&#8217;, which is of non-class type &#8216;int&#8217;
gdlpython.cpp: In function &#8216;BaseGDL* FromPython(PyObject*)&#8217;:
gdlpython.cpp:71: error: &#8216;NA_NumArrayCheck&#8217; was not declared in this scope
gdlpython.cpp:100: error: &#8216;PyArrayObject&#8217; was not declared in this scope
gdlpython.cpp:100: error: &#8216;array&#8217; was not declared in this scope
gdlpython.cpp:100: error: expected type-specifier before &#8216;PyArrayObject&#8217;
gdlpython.cpp:100: error: expected `>' before &#8216;PyArrayObject&#8217;
gdlpython.cpp:100: error: expected `(' before &#8216;PyArrayObject&#8217;
gdlpython.cpp:100: error: expected primary-expression before &#8216;>&#8217; token
gdlpython.cpp:100: error: expected `)' before &#8216;;&#8217; token
gdlpython.cpp:101: error: &#8216;NumarrayType&#8217; was not declared in this scope
gdlpython.cpp:101: error: expected `;' before &#8216;item_type&#8217;
gdlpython.cpp:104: error: &#8216;item_type&#8217; was not declared in this scope
gdlpython.cpp:104: error: &#8216;C_ARRAY&#8217; was not declared in this scope
gdlpython.cpp:104: error: &#8216;NA_InputArray&#8217; was not declared in this scope
gdlpython.cpp:131: error: &#8216;tUInt8&#8217; was not declared in this scope
gdlpython.cpp:133: error: &#8216;tInt16&#8217; was not declared in this scope
gdlpython.cpp:135: error: &#8216;tInt32&#8217; was not declared in this scope
gdlpython.cpp:137: error: &#8216;tFloat32&#8217; was not declared in this scope
gdlpython.cpp:139: error: &#8216;tFloat64&#8217; was not declared in this scope
gdlpython.cpp:141: error: &#8216;tComplex32&#8217; was not declared in this scope
gdlpython.cpp:145: error: &#8216;tComplex64&#8217; was not declared in this scope
gdlpython.cpp:149: error: &#8216;tUInt16&#8217; was not declared in this scope
gdlpython.cpp:151: error: &#8216;tUInt32&#8217; was not declared in this scope
datatypes.cpp: In member function &#8216;int Data_< <template-parameter-1-1> >::Scalar2index(SizeT&) const [with Sp = SpDByte]&#8217;:
datatypes.cpp:3723:   instantiated from here
datatypes.cpp:825: warning: comparison is always false due to limited range of data type
datatypes.cpp: In member function &#8216;SizeT Data_< <template-parameter-1-1> >::LoopIndex() const [with Sp = SpDByte]&#8217;:
datatypes.cpp:3723:   instantiated from here
datatypes.cpp:911: warning: comparison is always false due to limited range of data type
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDByte]&#8217;:
datatypes.cpp:3723:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDInt]&#8217;:
datatypes.cpp:3724:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
datatypes.cpp: In member function &#8216;int Data_< <template-parameter-1-1> >::Scalar2index(SizeT&) const [with Sp = SpDUInt]&#8217;:
datatypes.cpp:3725:   instantiated from here
datatypes.cpp:825: warning: comparison is always false due to limited range of data type
datatypes.cpp: In member function &#8216;SizeT Data_< <template-parameter-1-1> >::LoopIndex() const [with Sp = SpDUInt]&#8217;:
datatypes.cpp:3725:   instantiated from here
datatypes.cpp:911: warning: comparison is always false due to limited range of data type
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDUInt]&#8217;:
datatypes.cpp:3725:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDLong]&#8217;:
datatypes.cpp:3726:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDULong]&#8217;:
datatypes.cpp:3727:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDLong64]&#8217;:
datatypes.cpp:3728:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDULong64]&#8217;:
datatypes.cpp:3729:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDPtr]&#8217;:
datatypes.cpp:3730:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDFloat]&#8217;:
datatypes.cpp:3731:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDDouble]&#8217;:
datatypes.cpp:3732:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDString]&#8217;:
datatypes.cpp:3733:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDObj]&#8217;:
datatypes.cpp:3734:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDComplex]&#8217;:
datatypes.cpp:3735:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
topython.cpp: In member function &#8216;PyObject* Data_< <template-parameter-1-1> >::ToPython() [with Sp = SpDComplexDbl]&#8217;:
datatypes.cpp:3736:   instantiated from here
topython.cpp:99: error: &#8216;NA_vNewArray&#8217; was not declared in this scope
basic_op.cpp: In function &#8216;T pow(T, T) [with T = unsigned char]&#8217;:
basic_op.cpp:2832:   instantiated from &#8216;Data_<Sp2>* Data_< <template-parameter-1-1> >::Pow(BaseGDL*) [with Sp = SpDByte]&#8217;
datatypes.cpp:3723:   instantiated from here
basic_op.cpp:2801: warning: comparison is always false due to limited range of data type
basic_op.cpp: In function &#8216;T pow(T, T) [with T = short unsigned int]&#8217;:
basic_op.cpp:2832:   instantiated from &#8216;Data_<Sp2>* Data_< <template-parameter-1-1> >::Pow(BaseGDL*) [with Sp = SpDUInt]&#8217;
datatypes.cpp:3725:   instantiated from here
basic_op.cpp:2801: warning: comparison is always false due to limited range of data type
make[3]: *** [gdl-datatypes.o] Error 1
make[3]: Leaving directory `/home/kevin/gdl/gdl-0.9pre4/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kevin/gdl/gdl-0.9pre4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kevin/gdl/gdl-0.9pre4'
make: *** [all] Error 2


---

### Post by PaulFr on 2007-06-16
Looks like you're missing numarray. See the REQUIREMENTS section in README of gdl:

REQUIREMENTS:
Obligatory libraries:
plplot        [http://plplot.sourceforge.net/source/index.html](http://plplot.sourceforge.net/source/index.html)
gsl             [http://www.gnu.org/software/gsl](http://www.gnu.org/software/gsl)
readline    [http://ftp.gnu.org/pub/gnu/readline/readline-5.2.tar.gz](http://ftp.gnu.org/pub/gnu/readline/readline-5.2.tar.gz)

Optional libraries:
ImageMagick [http://www.imagemagick.org/www/download.html](http://www.imagemagick.org/www/download.html)
netCDF *)   [ftp://ftp.unidata.ucar.edu/pub/netcdf](ftp://ftp.unidata.ucar.edu/pub/netcdf)
HDF4 *)     [ftp://ftp.ncsa.uiuc.edu/HDF/HDF/HDF_Current](ftp://ftp.ncsa.uiuc.edu/HDF/HDF/HDF_Current)
HDF5        [ftp://ftp.ncsa.uiuc.edu/HDF/HDF5/current](ftp://ftp.ncsa.uiuc.edu/HDF/HDF5/current)
FFTW        [http://www.fftw.org/download.html](http://www.fftw.org/download.html)
python      [http://www.python.org](http://www.python.org)

Only with python:
numarray    [http://www.stsci.edu/resources/software_hardware/numarray](http://www.stsci.edu/resources/software_hardware/numarray)
matplotlib  [http://matplotlib.sourceforge.net](http://matplotlib.sourceforge.net)

---

### Post by hamburglar6 on 2007-06-16
It's all working now.  Thanks for the help, it's much appreciated.

---

