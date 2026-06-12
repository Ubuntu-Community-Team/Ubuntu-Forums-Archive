---
title: "How do I install Mapnik in Gutsy ?"
date: 2007-11-03
forum: General Help
---

### Post by haylocki on 2007-11-03
Hi, 

I am trying to install mapnik on my laptop.

I have downloaded the latest svn version of mapnik.

I ran 

```
./bootstrap
```

Which produced :

> Running libtoolize...
Running aclocal  -I config ...
Running autoheader...
Running automake...
Running autoconf ...
You could now exec ./configure --help to see available options

Then I ran 


```
./configure | grep -v yes
```

Which produced :

> checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... gawk
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for g++... g++
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
checking how to run the C++ preprocessor... g++ -E
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking for g++ option to produce PIC... -fPIC
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether to enable debugging... no
checking for pg_config... /usr/bin/pg_config
checking for pkg-config... /usr/bin/pkg-config
checking whether to enable included libxml2 building... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating include/mapnik/Makefile
config.status: creating plugins/Makefile
config.status: creating plugins/input/Makefile
config.status: creating plugins/input/gdal/Makefile
config.status: creating plugins/input/postgis/Makefile
config.status: creating plugins/input/raster/Makefile
config.status: creating plugins/input/shape/Makefile
config.status: creating src/Makefile
config.status: creating mapnik.pc
config.status: creating mapnik-uninstalled.pc
config.status: creating agg/Makefile
config.status: creating agg/src/Makefile
config.status: creating agg/include/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

Then I ran

```
make
```
```
sudo make install
```

Neither command produced any errors.

Then I ran :

```
sudo python scons/scons  PGSQL_INCLUDES=/usr/include/postgresql PGSQL_LIBS=/usr/lib/ PROJ_INCLUDES=/usr/include PROJ_LIBS=/usr/lib
```

Which produced :

> scons: Reading SConscript files ...
Building on Linux ...
Checking for C library m... (cached) yes
Checking for C library ltdl... (cached) yes
Checking for C library png... (cached) yes
Checking for C library tiff... (cached) yes
Checking for C library z... (cached) yes
Checking for C library jpeg... (cached) yes
Checking for C library proj... (cached) yes
Checking for C library pq... (cached) yes
Checking for C++ library gdal... (cached) yes
Checking for C++ library gigabase_r... (cached) no
Checking for C++ library boost_thread-mt... (cached) yes
Checking for C++ library boost_filesystem-mt... (cached) yes
Checking for C++ library boost_regex-mt... (cached) yes
Checking for C++ library boost_program_options-mt... (cached) yes
Bindings Python version... 2.5
Python 2.5 prefix... /usr
scons: done reading SConscript files.
scons: Building targets ...
scons: `.' is up to date.
scons: done building targets.

Then I ran

```
sudo python scons/scons install  PGSQL_INCLUDES=/usr/include/postgresql PGSQL_LIBS=/usr/lib/ PROJ_INCLUDES=/usr/include PROJ_LIBS=/usr
```

Which produced a similar output to the previous command.

I then try to run the c++ demo with :

```
g++ -O3 -I/usr/local/include/mapnik -I/opt/boost/include/boost-1_33_1 -I/usr/include/freetype2  -L/usr/local/lib -lmapnik rundemo.cpp -o rundemo
```

Which produced :

> rundemo.cpp: In function ‘int main(int, char**)’:
rundemo.cpp:45: error: ‘instance’ is not a member of ‘mapnik::freetype_engine’


How do I fix this error :confused:

Thanks, Ian

---

### Post by mvexel on 2008-02-25
I get stuck even sooner. The configure script does not get past boost detection. I got the 0.5.0 release off the website.

---

### Post by shmendrik on 2008-05-14
On hardy I installed mapnik 0.5.0 with some help from the instructions here:
[http://wiki.openstreetmap.org/index.php/Mapnik](http://wiki.openstreetmap.org/index.php/Mapnik)

the "Compiling the new Mapnik 0.5 from source on Debian Etch (stable)" section.

Things i needed to do to install on hardy included:
1)# ln -s libgdal1.4.0.so libgdal.so to be able to use GDAL.

2)to install, I did
```
scons/scons.py PGSQL_LIBS=/usr/lib/postgresql/8.3/lib PGSQL_INCLUDES=/usr/include/postgresql/
```
and then:
```
sudo scons/scons.py install PGSQL_LIBS=/usr/lib/postgresql/8.3/lib PGSQL_INCLUDES=/usr/include/postgresql/
```

Nothing worked until I did this step:
```
# echo "/usr/local/lib" >> /etc/ld.so.conf
# ldconfig
```
Tho I had to edit the file by hand.
All the pre-reqs I installed with apt-get.

I have not played around with it much yet, but rundemo.py works fine for me.

---

