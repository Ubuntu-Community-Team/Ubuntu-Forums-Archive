---
title: "cant compile C++ -in source packages -build-essential is instald+reinstald"
date: 2007-08-27
forum: General Help
---

### Post by of_darkness on 2007-08-27
> configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similar to libstdc++-dev.


listdc is installd n reinstalld as is c++ n all other build-essential packages who alredy was installd..  
And all other packages whom came upp in synaptic as instald when searching for the packages just 2 be on the safe side..

I have compild several packages before .. but now..


Kubuntu feisty fawn ,kde 3.5.7
 2.6.20-16-generic kernel
gcc    version 4;4,1.2-1ubuntu1
gcc-2,95 
gcc-3,3
gcc-3,4
gcc-3,4-base
gcc-4,1 
gcc-4,1-base
gcc-4,1-source
libstdc++5                    version: 1:3,3,6-15ubuntu1
libstdc++5-3,3-dev      version: 1:3,3,6-15ubuntu1
libstdc++6                    version: 4,1,2-0ubuntu4
libstdc++6-4,1-dbg      version: 4,1,2-0ubuntu4
libstdc++6-4,1-dev      version: 4,1,2-0ubuntu4
make                            version  3,81-3build1
dpkg-dev                     version  1,13,24ubuntu6

And as i final note i can say that i have tried to compile at least 3 totaly diffrent packages so script error can pobably be exkluded..

---

### Post by aJayRoo on 2007-08-27
Sorry to sound patronising but are you sure you have a C++ compiler installed? It is hard to tell exactly what is wrong without seeing the output of the configure command or the config.log file, perhaps you could post that file? It will be in the directory where the configure script is found. You could try installing the 'g++' package although it should be included with build-essential.

---

### Post by wirelessmonkey on 2007-08-28
Also, there's a realm of difference betweeen libstdc and libstdc++

---

### Post by of_darkness on 2007-08-28
> **wirelessmonkey said:**
> Also, there's a realm of difference betweeen libstdc and libstdc++ well name searching 4 libstdc in synaptic only results in libsdc++, and the are installd and its versions is listed in my previus post. 

packages   installed version
g++             version:  4:4,1,2-1ubuntu1
g++-3,3       version:  1:3.36-15ubuntu1
g++-4,1       version:  4,1,2-0ubuntu4

config log > Open project : /home/blutengel/kalarm-1.9.6beta/

Configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking whether system headers can cope with -O2 -fno-inline... irrelevant
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking whether accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... no
configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similar to libstdc++-dev.

Time : 46 seconds.


Configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking whether system headers can cope with -O2 -fno-inline... irrelevant
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking whether accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... no
configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similar to libstdc++-dev.

Time : 44 seconds.

 

---

### Post by of_darkness on 2007-08-28
> **aJayRoo said:**
> Sorry to sound patronising but are you sure you have a C++ compiler installed? It is hard to tell exactly what is wrong without seeing the output of the configure command or the config.log file, perhaps you could post that file? It will be in the directory where the configure script is found. You could try installing the 'g++' package although it should be included with build-essential.
well i thought 2 include g++ but was 2 tired 2se the relvence of it:P

well but yes i naturly checked all of that:P im not that newbie:P^^

But my gut feiling is that i have 2 versions of the compiler and it is that is messing upp it.. but that would be strange but heck im no programer so..

But any way look at my post above config log and versions of g++

---

### Post by of_darkness on 2007-08-28
> **aJayRoo said:**
> Sorry to sound patronising but are you sure you have a C++ compiler installed? It is hard to tell exactly what is wrong without seeing the output of the configure command or the config.log file, perhaps you could post that file? It will be in the directory where the configure script is found. You could try installing the 'g++' package although it should be included with build-essential.

I have found what the script is testing for that gives that output:

> ```
{ echo "$as_me:$LINENO: checking if C++ programs can be compiled" >&5
echo $ECHO_N "checking if C++ programs can be compiled... $ECHO_C" >&6; }
    if test "${kde_cv_stl_works+set}" = set; then
  echo $ECHO_N "(cached) $ECHO_C" >&6
else

      cat >conftest.$ac_ext <<_ACEOF
/* confdefs.h.  */
_ACEOF
cat confdefs.h >>conftest.$ac_ext
cat >>conftest.$ac_ext <<_ACEOF
/* end confdefs.h.  */

#include <string>
using namespace std;

int
main ()
{

  string astring="Hallo Welt.";
  astring.erase(0, 6); // now astring is "Welt"
  return 0;

  ;
  return 0;
}
_ACEOF
rm -f conftest.$ac_objext
if { (ac_try="$ac_compile"
case "(($ac_try" in
  *\"* | *\`* | *\\*) ac_try_echo=\$ac_try;;
  *) ac_try_echo=$ac_try;;
esac
eval "echo \"\$as_me:$LINENO: $ac_try_echo\"") >&5
  (eval "$ac_compile") 2>conftest.er1
  ac_status=$?
  grep -v '^ *+' conftest.er1 >conftest.err
  rm -f conftest.er1
  cat conftest.err >&5
  echo "$as_me:$LINENO: \$? = $ac_status" >&5
  (exit $ac_status); } && {
	 test -z "$ac_cxx_werror_flag" ||
	 test ! -s conftest.err
       } && test -s conftest.$ac_objext; then
  kde_cv_stl_works=yes
else
  echo "$as_me: failed program was:" >&5
sed 's/^/| /' conftest.$ac_ext >&5

	kde_cv_stl_works=no
fi

rm -f core conftest.err conftest.$ac_objext conftest.$ac_ext

fi


   { echo "$as_me:$LINENO: result: $kde_cv_stl_works" >&5
echo "${ECHO_T}$ *kde_cv_stl_works*" >&6; }

   if test "$kde_cv_stl_works" = "yes"; then
     # back compatible

cat >>confdefs.h <<_ACEOF
#define HAVE_SGI_STL 1
_ACEOF

   else
	 { { echo "$as_me:$LINENO: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similar to libstdc++-dev." >&5
echo "$as_me: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similar to libstdc++-dev." >&2;}
   { (exit 1); exit 1; }; }
   fi

   CXXFLAGS="$ac_save_CXXFLAGS"
   ac_ext=c
ac_cpp='$CPP $CPPFLAGS'
ac_compile='$CC -c $CFLAGS $CPPFLAGS conftest.$ac_ext >&5'
ac_link='$CC -o conftest$ac_exeext $CFLAGS $CPPFLAGS $LDFLAGS conftest.$ac_ext $LIBS >&5'
ac_compiler_gnu=$ac_cv_c_compiler_gnu
```
and the its is checking for kde_cv_stl that is the check taht fails and givs no compile error.. but what it is i have no ide..

and for version of g++ look at my other post today:) it is instald and reinstald

---

### Post by wirelessmonkey on 2007-08-28
I was able to compile Kalarm from source. Here are the libstdc packages I currently have installed.

libstdc++2.10-glibc2.2
libstdc++5
libstdc++6
libstdc++6-4.1-dev


Also, just happened to notice that they do have a current .deb package and an older version of Kalarm is available via Synaptic, in case you are unable to resolve the problem.


Good Luck!

---

### Post by of_darkness on 2007-08-28
> **wirelessmonkey said:**
> I was able to compile Kalarm from source. Here are the libstdc packages I currently have installed.

libstdc++2.10-glibc2.2
libstdc++5
libstdc++6
libstdc++6-4.1-dev


Also, just happened to notice that they do have a current .deb package and an older version of Kalarm is available via Synaptic, in case you are unable to resolve the problem.


Good Luck!

well the only package of those above that i diddent have was libstdc++2.10-glibc2.2 n i instaldit but 2 no avail.. same error..

hmm last i checked it it had deb for debian n as i dont rely know wich of them 2 chose i went 4 the source.. n i should be able 2 compile.. the only other person who have had this error vad solved by build-essentil meta package install but as i have it n tried 2 reinstall.. well if no one answers i guess il have 2 wait4 gutsy n kde4..

---

### Post by wirelessmonkey on 2007-08-28
You can install the .deb file on ubuntu.  Download it, then dpkg -i kalarm-blalba.deb

---

### Post by of_darkness on 2007-08-29
well i know that i can manualy install .deb done it alot of times.. that wasent the question.. the question was of brining in debian code as in a deb for debian..  if not the author says its okay so that i dosent create probs.

---

