---
title: "Unable to run Synaptic"
date: 2015-04-27
forum: General Help
---

### Post by Robbyx on 2015-04-27
I did a software update and I think it broke my ability to run synaptic.

Following other advice I ran the following:

> 
sudo dpkg --configure -a
sudo apt-get autoclean
sudo apt-get clean
sudo synaptic
terminate called after throwing an instance of 'Xapian::DatabaseCorruptError'


How do I resolve the DB corruption?

R

---

### Post by mc4man on 2015-04-27
you could try - 
```
sudo update-apt-xapian-index 
```
generally better to open synaptic with 
synaptic-pkexec

---

### Post by dino99 on 2015-04-27
Try:

> sudo dpkg-reconfigure apt-xapian-index

should do the trick, otherwise go for the brute way:

> sudo apt-get autoremove --purge apt-xapian-index 
sudo apt-get autoremove --purge  

this will remove apt-xapian-index and then python-xapian (needs to be reinstalled after logout/in)

---

### Post by Robbyx on 2015-04-27
> **dino99 said:**
> Try:
 otherwise go for the brute way:
this will remove apt-xapian-index and then python-xapian (needs to be reinstalled after logout/in)

I am struggling with installing python-xapian because "Since 1.2.16, release tarballs are compressed with xz instead of gzip,as it provides much better compression, without being too slow to
decompress.  (For now at least, Search::Xapian is still gzipped.)"


From the xapian d/l page it states:
> Debian and Ubuntu packages

Packages of xapian-core, xapian-omega, xapian-bindings (Python, Ruby, and Tcl), and the perl bindings (the package name is libsearch-xapian-perl) are available from the Debian and Ubuntu repositories. 

As I can not get into synaptic I am trying to follow this advice:

[https://community.webfaction.com/questions/72/problems-with-installing-xapian](https://community.webfaction.com/questions/72/problems-with-installing-xapian)

but that advice assumes that the downloads are gzip'd.

Could I please have some advice about how to install python-xapian's latest appropriate version which I assume is the stable one.

R

---

### Post by sudodus on 2015-04-27
You can expand tarballs that are xzipped with ***xzcat*** or directly with ***tar*** with the **J** option.

Example (extract from the file **ball.tar.xz**)

```
tar -xvJf ball.tar.xz
```

---

### Post by Robbyx on 2015-04-27
g++ found

---

### Post by Robbyx on 2015-04-27
I have just rechecked if I can get into synaptic and I can now do so. I assume I have to continue with the binding not withstanding that synaptic is now working and I have not been able to make the latest bindings. Can I stop  trying to complete the new bindings because I am unable to find the fault that is preventing the binding from proceeding?


Configure is reporting a problem about the correct library but I can not see the fault and so can not proceed to make the bindings. The error report is coming as a result of running 

```
./configure --prefix=$HOME \
PYTHON=/usr/bin/python3.4 \
PYTHON_LIB=$HOME/lib/python3.4 \
--with-python --without-ruby \
--without-php --without-tcl
```

This is the error report taken from the quoted output below
[I]checking /usr/bin/python3.4 version... 3.4 (too new - use --with-python3 for Python 3 support)
configure: error: Use --with-python3 for Python 3 support (/usr/bin/python3.4 is 3.4)[/I]


This is the original  instructions altered by me  for the versions I am installing and their locations:
> mkdir -p ~/bin ~/src ~/lib/python3.4
cd ~/src
wget [http://oligarchy.co.uk/xapian/1.3.2/xapian-core-1.3.2.tar.xz](http://oligarchy.co.uk/xapian/1.3.2/xapian-core-1.3.2.tar.xz)
tar -zvJf xapian-core-1.3.2.tar.xz
cd xapian-core-1.3.2
./configure --prefix=$HOME
make
make install
cd ..
wget [http://oligarchy.co.uk/xapian/1.3.2/xapian-bindings-1.3.2.tar.xz](http://oligarchy.co.uk/xapian/1.3.2/xapian-bindings-1.3.2.tar.xz)
tar -zvJf xapian-bindings-1.3.2.tar.xz
cd xapian-bindings-1.3.2
./configure --prefix=$HOME \
PYTHON=/usr/bin/python3.4 \
PYTHON_LIB=$HOME/lib/python3.4 \
--with-python --without-ruby \
--without-php --without-tcl
make
make install


[I]I have only  successfully reached the end of the following lines taken from the above instructions:
cd ..
wget [http://oligarchy.co.uk/xapian/1.3.2/xapian-bindings-1.3.2.tar.xz](http://oligarchy.co.uk/xapian/1.3.2/xapian-bindings-1.3.2.tar.xz)
tar -zvJf xapian-bindings-1.3.2.tar.xz
cd xapian-bindings-1.3.2
[/I]


Prior to make install the $HOME/lib/python3.4 \  is it  ok for the python_lib to be empty?
```
robins@robins-EP35-DS3L:~/src/xapian-bindings-1.3.2$ ./configure --prefix=$HOME PYTHON=/usr/bin/python3.4 PYTHON_LIB=$HOME/lib/python3.4 --with-python --without-ruby --without-php --without-tcl
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether UID '1000' is supported by ustar format... yes
checking whether GID '1000' is supported by ustar format... yes
checking how to create a ustar tar archive... gnutar
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for a working dd... /bin/dd
checking how to truncate binary pipes... /bin/dd bs=4096 count=1
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for xapian-config... /usr/bin/xapian-config
checking /usr/bin/xapian-config works... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for /usr/bin/python3.4... /usr/bin/python3.4
checking /usr/bin/python3.4 version... 3.4 (too new - use --with-python3 for Python 3 support)
configure: error: Use --with-python3 for Python 3 support (/usr/bin/python3.4 is 3.4)
robins@robins-EP35-DS3L:~/src/xapian-bindings-1.3.2$ 

```

R

---

### Post by Robbyx on 2015-04-27
PS
Although synaptic seems to be working Congruity is not loading in firefox and this is what started me off trying to get into synaptic. I have done a reinstall and still congruity is not being called from within firefox when I go into the logiteck harmony web site to update my remote.

---

### Post by Robbyx on 2015-04-28
I have opened a new thread on the outstanding points.

---

