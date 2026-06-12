---
title: "How do I install the latest version of Beagle?"
date: 2008-03-23
forum: General Help
---

### Post by Robbyx on 2008-03-23
From the normal repositories I am only getting 2.16.3

I would appreciate some help in installing the latest version as I think not all my files are being indexed and so are not being found on a search. I am not referring the 100 file normal limit.

Robin

---

### Post by kellemes on 2008-03-23
You have to build from source..
[http://beagle-project.org/Installing_Beagle]("http://beagle-project.org/Installing_Beagle")

---

### Post by Robbyx on 2008-03-23
Thank you. Can you please suggest how I deal with c compiler error?

```
robin@robin:/tmp/beagle$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
robin@robin:/tmp/beagle$ 

```

I was not able to find the config.log as I do not know where to look for it. However looking at other posts those who have found it are none the wiser.

Robin

---

### Post by dbera on 2008-03-23
config.log can be found in the directory where configure is i.e. /tmp/beagle in your case.

---

### Post by dbera on 2008-03-23
I did a quick search and people seem to suggest installing build-essentials, libc6-dev-i386.

---

### Post by kellemes on 2008-03-23
```
sudo apt-get install build-essential
```

---

### Post by Robbyx on 2008-03-23
Thank you everyone for your great help. I am almost there, I think, but not quite.
This is the tail end of the install response in Terminal. I have installed sqlite3 v3.4.2-1build1 from  synaptec and yet the Beagle install is saying I need to install it. I wonder it is a different package that needs installing instead of the obvious sqlite3 in synaptec. Any ideas?

> checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for SQLITE3... no
configure: error: You need to install sqlite >= 3.3.1
robin@robin:/tmp/beagle$ sudo apt-get install build-essential


---

### Post by dbera on 2008-03-23
Probably you need the devel package.

---

### Post by Robbyx on 2008-03-23
If I get this working I think I have another problem. Beagle likes to use extended attributes. My main document partition is using ntfs. I do not know if it uses extended attributes that are useable in Ubuntu. Here is something I found:

> My understanding is that alternate data streams was implimented (at the filesystem level, btw) in NTFS to provide compatibility with Mac's HFS (Hierarchical File System). In the HFS files are stored with 2 parts: the content data (ie text, audio, etc) and the resource data (used to identify file type and other pertinent details(EA's)). In NTFS files have 2 data streams: the content data stream (for the file's contents) and the alternate data stream - where all the meta-data is forked (EA's).



I have just had a look at man mount and it does not mention any extended attributes for ntfs so I assume there are none available in Gutsy for ntfs!  Have I understood the position correctly?

---

### Post by Robbyx on 2008-03-23
> **dbera said:**
> Probably you need the devel package.

Do you know what it is called because I can not see it in my version of synaptic.

---

### Post by Steveway on 2008-03-23
The build-dep command is made for this purpose, it will fetch all packages needed for compilation.
sudo apt-get build-dep beagle

---

### Post by dbera on 2008-03-23
dpkg-query -W *sqlite*

---

### Post by dbera on 2008-03-23
> **Robbyx said:**
> If I get this working I think I have another problem. Beagle likes to use extended attributes. My main document partition is using ntfs. I do not know if it uses extended attributes that are useable in Ubuntu. Here is something I found:


Beagle can work without extended attributes. See FAQ [http://beagle-project.org/FAQ](http://beagle-project.org/FAQ)

---

### Post by Robbyx on 2008-03-23
> **Steveway said:**
> The build-dep command is made for this purpose, it will fetch all packages needed for compilation.
sudo apt-get build-dep beagle

After following the command line you suggested I rant the Beagle install command:

```
robin@robin:/tmp/beagle$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
checking the maximum length of command line arguments... 98304
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
checking dynamic linker characteristics... GNU/Linux ld.so
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking for bash... /bin/bash
checking for zip... /usr/bin/zip
checking for mono... /usr/bin/mono
checking for gmcs... /usr/bin/gmcs
checking for mono.pc... found
checking pkg-config is at least version 0.9.0... yes
checking for MONO... yes
checking for Mono.Data.Sqlite.dll... found
checking for Mono.Posix.dll... found
checking for System.Data.dll... found
checking for System.Web.dll... found
checking for ICSharpCode.SharpZipLib.dll... found
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for desktop-launch... no
checking for xdg-open... /usr/bin/xdg-open
checking for intltool >= 0.23... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  ar bg ca cs da de dz el en_CA en_GB es eu fi fr gl he hi hu it ja ka ko lt lv mk nb nl oc pa pl pt pt_BR ru sl sr sr@Latn sv th tr uk vi zh_CN zh_HK zh_TW
checking for SQLITE3... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking X11/extensions/scrnsaver.h usability... yes
checking X11/extensions/scrnsaver.h presence... yes
checking for X11/extensions/scrnsaver.h... yes
checking for XScreenSaverQueryExtension in -lXss... yes
checking for GNOME_VFS... yes
checking for BEAGLE_UI... yes
checking for UIGLUE... yes
checking for LIBTRAYICON... yes
checking for OPEN_WITH... yes
checking for EVO... yes
checking for GSF_SHARP... yes
checking for WV1... yes
checking for TAGLIB_SHARP... no
checking for LIBEXIF... yes
checking for LIBEXIF_API_CHECK... yes
checking for LIBEXIF_VERSION_CHECK... yes
checking for BEAGLED... yes
checking for Epiphany... 
checking for Epiphany 2.20... no
checking for Epiphany 2.19... no
checking for Epiphany 2.18... no
checking for Epiphany 2.17... no
checking for Epiphany 2.16... no
checking for Epiphany 2.15... no
checking for Epiphany 2.14... no
checking for Epiphany 1.8... no
checking for Epiphany 1.6... no
checking for GALAGO... no
checking for AVAHI_SHARP... no
checking for kde-config... /usr/bin/kde-config
checking for chm_open in -lchm... no
checking for monodocer... no
configure: error: You need to install monodoc, or pass --disable-docs to configure to skip documentation installation
robin@robin:/tmp/beagle$ 

```

Look at all number of negative results!

Robin

---

### Post by Robbyx on 2008-03-23
May be the sqlite problem has gone because it does not appear in the latest install results set out above by me after running 

sudo apt-get build-dep beagle

> **dbera said:**
> dpkg-query -W *sqlite*

```
robin@robin:/tmp/beagle$ dpkg-query -W *sqlite*
libgda3-sqlite
libmono-sqlite2.0-cil   1.2.4-6ubuntu6.1
libsqlite0
libsqlite3-0    3.4.2-1build1
libsqlite3-dev  3.4.2-1build1
libsqliteodbc
python-pysqlite2        2.3.4-2
python-pysqlite2-dbg
python2.3-pysqlite2
python2.4-pysqlite2
python2.5-pysqlite2
sqlite3 3.4.2-1build1
sqlite3-doc
robin@robin:/tmp/beagle$ 


```

---

### Post by Robbyx on 2008-03-24
Thank you everyone for your further help. Much appreciated. I added the missing doc file and the installation went through without a hitch. I ran search and it still shows as 2.16.3

Does this report at the end of the installation give any clue as to why 3 is not showing as the version in the search help drop down

>        Beagle version:           0.3.0
        Target OS:                linux
        Inotify:                  yes

        Prefix:                   /usr/local
        GNOME prefix:             /usr
        KDE prefix:               /usr

        evolution-sharp?          yes
        gsf-sharp?                yes
        galago-sharp?             no
        avahi-sharp               no (missing dependencies)
        wv1?                      yes
        libchm?                   no

        Firefox Extension?        yes
        Epiphany Extension?       no (Epiphany not installed)
        Thunderbird Extension?    yes

        Local taglib-sharp?       yes

        Monitor screensaver       yes
        beagle-search GUI         yes

        Build docs?               yes



Robin

---

### Post by dbera on 2008-03-24
> **Robbyx said:**
> Thank you everyone for your further help. Much appreciated. I added the missing doc file and the installation went through without a hitch. I ran search and it still shows as 2.16.3


Possibly wrong prefix - the installation report says /usr/local but you system might be installing everything in /usr To not break anything in ubuntu, you should pass these usual configure options
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var ...

But first sure your prefix is indeed /usr (i.e. you dont have lots of files in /usr/local/bin, /usr/local/etc and others).

---

### Post by Robbyx on 2008-03-24
> ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var ...

Can you please confirm that the 3 dots go on the end or should I be adding some other strings and you assumed I would know which ones to add.

Robin

---

### Post by dbera on 2008-03-24
> **Robbyx said:**
> Can you please confirm that the 3 dots go on the end or should I be adding some other strings and you assumed I would know which ones to add.


hehe :) do not use "..." at the end, instead replace it with whatever parameters you were using for ./configure earlier (if any).

---

### Post by Robbyx on 2008-03-24
> ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

I checked the other directories and they did not contain much so I ran the above script as is. It has made no difference to what is loaded on a search. It is still 2.16. The tail end of the installation states:

> Beagle version:           0.3.0
        Target OS:                linux
        Inotify:                  yes

        Prefix:                   /usr
        GNOME prefix:             /usr
        KDE prefix:               /usr

        evolution-sharp?          yes
        gsf-sharp?                yes
        galago-sharp?             no
        avahi-sharp               no (missing dependencies)
        wv1?                      yes
        libchm?                   no

        Firefox Extension?        yes
        Epiphany Extension?       no (Epiphany not installed)
        Thunderbird Extension?    yes

        Local taglib-sharp?       yes

        Monitor screensaver       yes
        beagle-search GUI         yes

        Build docs?               yes



Also I am not seeing an extension in Firefox that correlates with Search or Beagle. I wonder if that has failed as well. 

Any ideas how to get this extraction over with?

Robin

---

### Post by dbera on 2008-03-24
> **Robbyx said:**
> I checked the other directories and they did not contain much so I ran the above script as is. It has made no difference to what is loaded on a search. It is still 2.16. The tail end of the installation states:
...
Also I am not seeing an extension in Firefox that correlates with Search or Beagle. I wonder if that has failed as well. 


Did you uninstall the previous installations ? 

1.  if you had a package installed, remove it

2. Remove old installation from /usr/local
$ cd /tmp/beagle
$ rm config.cache
$ ./configure
$ make clean
$ make
$ sudo make uninstall

3. Now install the correct one
$ rm config.cache
$./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
$ make clean
$ make
$ sudo make install

It should work one. It not generally that complicated, it because it by mistake installed it in a different prefix and then did not run make clean before running make again.

I seriously recommend using apt-get source to deal with installing from source. It will get the dependencies automatically and also build the source for you. Of course this is if you have correct version in your ubuntu repo.

---

### Post by Robbyx on 2008-03-25
> I seriously recommend using apt-get source to deal with installing from source. It will get the dependencies automatically and also build the source for you. Of course this is if you have correct version in your ubuntu repo.

Thank you for your detailed and hopefully very helpful reply.  I will follow your advice and that should be the end of my problem.

The Ubuntu repo that I access via synaptec has the 2.16.3  version. I would not have had any of these problems if someone had updated the repo. Maybe it is in another repo but I do not know about it.

Robin

---

### Post by dbera on 2008-03-25
> **Robbyx said:**
> Thank you for your detailed and hopefully very helpful reply.  I will follow your advice and that should be the end of my problem.

The Ubuntu repo that I access via synaptec has the 2.16.3  version. I would not have had any of these problems if someone had updated the repo. Maybe it is in another repo but I do not know about it.

Robin

BTW, I noticed you are trying to build 0.3.0. Since the current version is 0.3.4, you might want to try any of the higher versions. Since you are building from source yourself, you might as well build the most recent one :)

---

### Post by Robbyx on 2008-03-25
Many of the commands in your list of steps to follow produced responses such as no file available eg config.cache.

I continued on with the install of the latest version. At the end of the install it reported:

> checking for NDESK_DBUS... configure: error: Package requirements (ndesk-dbus-1.0 >= 0.5.2) were not met:

Requested 'ndesk-dbus-1.0 >= 0.5.2' but version of NDesk.DBus is 0.4.2
You may find new versions of NDesk.DBus at [http://www.ndesk.org/DBusSharp](http://www.ndesk.org/DBusSharp)

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NDESK_DBUS_CFLAGS
and NDESK_DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I tried to install ndesk_dbus
Install worked
I think that make worked. It did report that 'nothing to be done  for 'all-am' ' but ignored it.
Make install did not work:
> robin@robin:~/ndesk-dbus-0.6.1a$ make install
Making install in src
make[1]: Entering directory `/home/robin/ndesk-dbus-0.6.1a/src'
make[2]: Entering directory `/home/robin/ndesk-dbus-0.6.1a/src'
make[2]: Nothing to be done for `install-exec-am'.
/usr/bin/gacutil /i NDesk.DBus.dll /f /gacdir /usr/local/lib
Failure adding assembly to the cache: gac directories could not be created, possibly permission issues.
make[2]: *** [install-data-local] Error 1
make[2]: Leaving directory `/home/robin/ndesk-dbus-0.6.1a/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/robin/ndesk-dbus-0.6.1a/src'
make: *** [install-recursive] Error 1
robin@robin:~/ndesk-dbus-0.6.1a$ 


Any comments?
BTW is version 3.4 available in a repository somewhere?

---

### Post by dbera on 2008-03-25
> **Robbyx said:**
> Many of the commands in your list of steps to follow produced responses such as no file available eg config.cache.
Thats ok. Those are safety checks.

> Make install did not work:
you always have to do "sudo make install" since make install needs roots access.

> BTW is version 3.4 available in a repository somewhere?
[http://ftp.gnome.org/pub/GNOME/sources/beagle/0.3/](http://ftp.gnome.org/pub/GNOME/sources/beagle/0.3/)

---

### Post by Robbyx on 2008-03-25
Repository
[http://ftp.gnome.org/pub/GNOME/sources/beagle/0.3/](http://ftp.gnome.org/pub/GNOME/sources/beagle/0.3/)
I think that is just a download site. What I was hoping for was a repo that I could add into synaptec and it would deal with all the dependencies, etc.

---

### Post by Robbyx on 2008-03-25
I can not tell if the Beagle installation worked.  An enormous amount of code was generated in the terminal. I think it went through ok, but I can not load Beagle. I tried $beagled. That did not work. The search icon does not work. Where do I go to start beagle?

Thanks for your patience.

---

### Post by Robbyx on 2008-03-25
Correction:

The ordinary search in places does work. My old Beagle icon does not.

---

### Post by Robbyx on 2008-03-25
Terminal output:

I thought I had better post the output even though it is a lot:

```
./Settings.cs(1496,33): warning CS0414: The private field `SettingsDialog.AddHostDialog.found_iter' is assigned but its value is never used
Compilation succeeded - 25 warning(s)
/usr/bin/gmcs -debug -out:DocExtractor.exe  ./DocExtractor.cs -r:/usr/lib/cli/gmime-sharp-2.2/gmime-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/cli/gsf-sharp-0.0/gsf-sharp.dll   -r:Mono.Posix -r:../Util/Util.dll -r:../BeagleClient/Beagle.dll -r:../beagled/BeagleDaemonLib.dll
sed -e "s|\@prefix\@|/usr|g" -e "s|\@pkglibdir\@|/usr/lib/beagle|g" -e "s|\@libdir\@|/usr/lib|g" -e "s|\@libexecdir\@|/usr/libexec|g" -e "s|\@bindir\@|/usr/bin|g" -e "s|\@sbindir\@|/usr/sbin|g" -e "s|\@sysconfdir\@|/etc|g" -e "s|\@localstatedir\@|/var|g" -e "s|\@gacprefix\@|/usr|g" -e "s|\@bash\@|/bin/bash|" -e "s|\@target\@|Info.exe|g" < ./wrapper.in > beagle-info
chmod +x beagle-info
sed -e "s|\@prefix\@|/usr|g" -e "s|\@pkglibdir\@|/usr/lib/beagle|g" -e "s|\@libdir\@|/usr/lib|g" -e "s|\@libexecdir\@|/usr/libexec|g" -e "s|\@bindir\@|/usr/bin|g" -e "s|\@sbindir\@|/usr/sbin|g" -e "s|\@sysconfdir\@|/etc|g" -e "s|\@localstatedir\@|/var|g" -e "s|\@gacprefix\@|/usr|g" -e "s|\@bash\@|/bin/bash|" -e "s|\@target\@|Shutdown.exe|g" < ./wrapper.in > beagle-shutdown
chmod +x beagle-shutdown
sed -e "s|\@prefix\@|/usr|g" -e "s|\@pkglibdir\@|/usr/lib/beagle|g" -e "s|\@libdir\@|/usr/lib|g" -e "s|\@libexecdir\@|/usr/libexec|g" -e "s|\@bindir\@|/usr/bin|g" -e "s|\@sbindir\@|/usr/sbin|g" -e "s|\@sysconfdir\@|/etc|g" -e "s|\@localstatedir\@|/var|g" -e "s|\@gacprefix\@|/usr|g" -e "s|\@bash\@|/bin/bash|" -e "s|\@target\@|Query.exe|g" < ./wrapper.in > beagle-query
chmod +x beagle-query
sed -e "s|\@prefix\@|/usr|g" -e "s|\@pkglibdir\@|/usr/lib/beagle|g" -e "s|\@libdir\@|/usr/lib|g" -e "s|\@libexecdir\@|/usr/libexec|g" -e "s|\@bindir\@|/usr/bin|g" -e "s|\@sbindir\@|/usr/sbin|g" -e "s|\@sysconfdir\@|/etc|g" -e "s|\@localstatedir\@|/var|g" -e "s|\@gacprefix\@|/usr|g" -e "s|\@bash\@|/bin/bash|" -e "s|\@target\@|StaticQuery.exe|g" < ./wrapper.in > beagle-static-query
chmod +x beagle-static-query
sed -e "s|\@prefix\@|/usr|g" -e "s|\@pkglibdir\@|/usr/lib/beagle|g" -e "s|\@libdir\@|/usr/lib|g" -e "s|\@libexecdir\@|/usr/libexec|g" -e "s|\@bindir\@|/usr/bin|g" -e "s|\@sbindir\@|/usr/sbin|g" -e "s|\@sysconfdir\@|/etc|g" -e "s|\@localstatedir\@|/var|g" -e "s|\@gacprefix\@|/usr|g" -e "s|\@bash\@|/bin/bash|" -e "s|\@target\@|Config.exe|g" < ./wrapper.in > beagle-config
chmod +x beagle-config
sed -e "s|\@prefix\@|/usr|g" -e "s|\@pkglibdir\@|/usr/lib/beagle|g" -e "s|\@libdir\@|/usr/lib|g" -e "s|\@libexecdir\@|/usr/libexec|g" -e "s|\@bindir\@|/usr/bin|g" -e "s|\@sbindir\@|/usr/sbin|g" -e "s|\@sysconfdir\@|/etc|g" -e "s|\@localstatedir\@|/var|g" -e "s|\@gacprefix\@|/usr|g" -e "s|\@bash\@|/bin/bash|" -e "s|\@target\@|Settings.exe|g" < ./wrapper.in > beagle-settings
chmod +x beagle-settings
sed -e "s|\@prefix\@|/usr|g" -e "s|\@pkglibdir\@|/usr/lib/beagle|g" -e "s|\@libdir\@|/usr/lib|g" -e "s|\@libexecdir\@|/usr/libexec|g" -e "s|\@bindir\@|/usr/bin|g" -e "s|\@sbindir\@|/usr/sbin|g" -e "s|\@sysconfdir\@|/etc|g" -e "s|\@localstatedir\@|/var|g" -e "s|\@gacprefix\@|/usr|g" -e "s|\@bash\@|/bin/bash|" -e "s|\@target\@|DocExtractor.exe|g" < ./wrapper.in > beagle-doc-extractor
chmod +x beagle-doc-extractor
sed -e "s|\@prefix\@|/usr|g" -e "s|\@pkglibdir\@|/usr/lib/beagle|g" -e "s|\@libdir\@|/usr/lib|g" -e "s|\@libexecdir\@|/usr/libexec|g" -e "s|\@bindir\@|/usr/bin|g" -e "s|\@sbindir\@|/usr/sbin|g" -e "s|\@sysconfdir\@|/etc|g" -e "s|\@localstatedir\@|/var|g" -e "s|\@gacprefix\@|/usr|g" -e "s|\@bash\@|/bin/bash|" < ./beagle-crawl-system.in > beagle-crawl-system
chmod +x beagle-crawl-system
make[2]: Leaving directory `/home/robin/beagle/tools'
Making all in conf-data
make[2]: Entering directory `/home/robin/beagle/conf-data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/robin/beagle/conf-data'
Making all in thunderbird-extension
make[2]: Entering directory `/home/robin/beagle/thunderbird-extension'
zip -q9 chrome/beagle.jar content/beagle.css content/beagleIndexer.js content/beagleMailWindow.xul content/beagleMessenger.xul content/beaglePrefs.xul content/beagleQueue.js content/beagleService.js content/beagleSettings.js content/beagleUnindex.js content/beagleUnindex.xul content/beagleUtils.js content/contents.rdf locale/en-US/beagle.dtd locale/en-US/strings.properties locale/en-US/contents.rdf skin/classic/overlay.css skin/classic/beagle.png skin/classic/beagle-disabled.png skin/classic/beagle-error.png skin/classic/contents.rdf
zip -q9 beagle.xpi chrome.manifest install.rdf chrome/beagle.jar defaults/preferences/default.js components/BeagleIndexer.js components/BeagleQueue.js components/BeagleSettings.js components/BeagleCommandLine.js
make[2]: Leaving directory `/home/robin/beagle/thunderbird-extension'
make[2]: Entering directory `/home/robin/beagle'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/robin/beagle'
make[1]: Leaving directory `/home/robin/beagle'
robin@robin:~/beagle$ sudo make install
Making install in Util
make[1]: Entering directory `/home/robin/beagle/Util'
make[2]: Entering directory `/home/robin/beagle/Util'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/lib/beagle
mkdir -p -- /usr/lib/beagle
/usr/bin/install -c -m 644 Util.dll Util.dll.mdb Util.dll.config /usr/lib/beagle
/usr/bin/install -c -m 644 UiUtil.dll UiUtil.dll.mdb ./UiUtil.dll.config /usr/lib/beagle
make[2]: Leaving directory `/home/robin/beagle/Util'
make[1]: Leaving directory `/home/robin/beagle/Util'
Making install in glue
make[1]: Entering directory `/home/robin/beagle/glue'
make[2]: Entering directory `/home/robin/beagle/glue'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/beagle" || /bin/mkdir -p "/usr/lib/beagle"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libbeagleglue.la' '/usr/lib/beagle/libbeagleglue.la'
/usr/bin/install -c .libs/libbeagleglue.so.0.0.0 /usr/lib/beagle/libbeagleglue.so.0.0.0
(cd /usr/lib/beagle && { ln -s -f libbeagleglue.so.0.0.0 libbeagleglue.so.0 || { rm -f libbeagleglue.so.0 && ln -s libbeagleglue.so.0.0.0 libbeagleglue.so.0; }; })
(cd /usr/lib/beagle && { ln -s -f libbeagleglue.so.0.0.0 libbeagleglue.so || { rm -f libbeagleglue.so && ln -s libbeagleglue.so.0.0.0 libbeagleglue.so; }; })
/usr/bin/install -c .libs/libbeagleglue.lai /usr/lib/beagle/libbeagleglue.la
/usr/bin/install -c .libs/libbeagleglue.a /usr/lib/beagle/libbeagleglue.a
chmod 644 /usr/lib/beagle/libbeagleglue.a
ranlib /usr/lib/beagle/libbeagleglue.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/beagle
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/beagle

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libbeagleuiglue.la' '/usr/lib/beagle/libbeagleuiglue.la'
/usr/bin/install -c .libs/libbeagleuiglue.so.0.0.0 /usr/lib/beagle/libbeagleuiglue.so.0.0.0
(cd /usr/lib/beagle && { ln -s -f libbeagleuiglue.so.0.0.0 libbeagleuiglue.so.0 || { rm -f libbeagleuiglue.so.0 && ln -s libbeagleuiglue.so.0.0.0 libbeagleuiglue.so.0; }; })
(cd /usr/lib/beagle && { ln -s -f libbeagleuiglue.so.0.0.0 libbeagleuiglue.so || { rm -f libbeagleuiglue.so && ln -s libbeagleuiglue.so.0.0.0 libbeagleuiglue.so; }; })
/usr/bin/install -c .libs/libbeagleuiglue.lai /usr/lib/beagle/libbeagleuiglue.la
/usr/bin/install -c .libs/libbeagleuiglue.a /usr/lib/beagle/libbeagleuiglue.a
chmod 644 /usr/lib/beagle/libbeagleuiglue.a
ranlib /usr/lib/beagle/libbeagleuiglue.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/beagle
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/beagle

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/robin/beagle/glue'
make[1]: Leaving directory `/home/robin/beagle/glue'
Making install in BeagleClient
make[1]: Entering directory `/home/robin/beagle/BeagleClient'
make[2]: Entering directory `/home/robin/beagle/BeagleClient'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/lib/beagle
/usr/bin/install -c -m 644 Beagle.dll Beagle.dll.mdb /usr/lib/beagle
make[2]: Leaving directory `/home/robin/beagle/BeagleClient'
make[1]: Leaving directory `/home/robin/beagle/BeagleClient'
Making install in beagled
make[1]: Entering directory `/home/robin/beagle/beagled'
make[2]: Entering directory `/home/robin/beagle/beagled'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/etc/xdg/autostart" || /bin/mkdir -p "/etc/xdg/autostart"
 /usr/bin/install -c -m 644 'beagled-autostart.desktop' '/etc/xdg/autostart/beagled-autostart.desktop'
/bin/bash ../mkinstalldirs /usr/bin
/bin/bash ../mkinstalldirs /usr/sbin
/bin/bash ../mkinstalldirs /usr/lib/beagle
/bin/bash ../mkinstalldirs /usr/share/beagle
mkdir -p -- /usr/share/beagle
/bin/bash ../mkinstalldirs /usr/lib/beagle/Backends
mkdir -p -- /usr/lib/beagle/Backends
/usr/bin/install -c -m 644 EvolutionBackends.dll EvolutionBackends.dll.mdb /usr/lib/beagle/Backends
/usr/bin/install -c beagled.tmp /usr/bin/beagled
/usr/bin/install -c beagle-extract-content.tmp /usr/bin/beagle-extract-content
/usr/bin/install -c beagle-build-index.tmp /usr/sbin/beagle-build-index
/usr/bin/install -c beagle-dump-index.tmp /usr/sbin/beagle-dump-index
/usr/bin/install -c beagle-manage-index.tmp /usr/sbin/beagle-manage-index
/usr/bin/install -c beagle-master-delete-button.tmp /usr/sbin/beagle-master-delete-button
/usr/bin/install -c beagled-index-helper.tmp /usr/lib/beagle/beagled-index-helper
/usr/bin/install -c -m 644 BeagleDaemonPlugins.dll                 /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemonPlugins.dll.mdb             /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemonLib.dll             /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemonLib.dll.mdb         /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemon.exe                 /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemon.exe.mdb             /usr/lib/beagle
/usr/bin/install -c -m 644 ExtractContent.exe        /usr/lib/beagle
/usr/bin/install -c -m 644 ExtractContent.exe.mdb    /usr/lib/beagle
/usr/bin/install -c -m 644 IndexHelper.exe           /usr/lib/beagle
/usr/bin/install -c -m 644 IndexHelper.exe.mdb       /usr/lib/beagle
/usr/bin/install -c -m 644 BuildIndex.exe            /usr/lib/beagle
/usr/bin/install -c -m 644 BuildIndex.exe.mdb        /usr/lib/beagle
/usr/bin/install -c -m 644 DumpIndex.exe             /usr/lib/beagle
/usr/bin/install -c -m 644 DumpIndex.exe.mdb         /usr/lib/beagle
/usr/bin/install -c -m 644 ManageIndex.exe           /usr/lib/beagle
/usr/bin/install -c -m 644 ManageIndex.exe.mdb       /usr/lib/beagle
/usr/bin/install -c -m 644 ThunderbirdBackends.dll                 /usr/lib/beagle/Backends
/usr/bin/install -c -m 644 ThunderbirdBackends.dll.mdb             /usr/lib/beagle/Backends
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './beagled.1' '/usr/share/man/man1/beagled.1'
 /usr/bin/install -c -m 644 './beagle-dump-index.1' '/usr/share/man/man1/beagle-dump-index.1'
test -z "/usr/share/man/man8" || /bin/mkdir -p "/usr/share/man/man8"
 /usr/bin/install -c -m 644 './beagle-build-index.8' '/usr/share/man/man8/beagle-build-index.8'
 /usr/bin/install -c -m 644 './beagle-extract-content.8' '/usr/share/man/man8/beagle-extract-content.8'
 /usr/bin/install -c -m 644 './beagle-imlogviewer.8' '/usr/share/man/man8/beagle-imlogviewer.8'
 /usr/bin/install -c -m 644 './beagle-manage-index.8' '/usr/share/man/man8/beagle-manage-index.8'
test -z "/usr/share/beagle/webinterface" || /bin/mkdir -p "/usr/share/beagle/webinterface"
 /usr/bin/install -c -m 644 './webinterface/index.xml' '/usr/share/beagle/webinterface/index.xml'
 /usr/bin/install -c -m 644 './webinterface/default.js' '/usr/share/beagle/webinterface/default.js'
 /usr/bin/install -c -m 644 './webinterface/propname-table.js' '/usr/share/beagle/webinterface/propname-table.js'
 /usr/bin/install -c -m 644 './webinterface/help.html' '/usr/share/beagle/webinterface/help.html'
 /usr/bin/install -c -m 644 './webinterface/mappings.xml' '/usr/share/beagle/webinterface/mappings.xml'
 /usr/bin/install -c -m 644 './webinterface/opensearch.xml' '/usr/share/beagle/webinterface/opensearch.xml'
 /usr/bin/install -c -m 644 './webinterface/index.xsl' '/usr/share/beagle/webinterface/index.xsl'
 /usr/bin/install -c -m 644 './webinterface/hitresult.xsl' '/usr/share/beagle/webinterface/hitresult.xsl'
 /usr/bin/install -c -m 644 './webinterface/statusresult.xsl' '/usr/share/beagle/webinterface/statusresult.xsl'
 /usr/bin/install -c -m 644 './webinterface/default.css' '/usr/share/beagle/webinterface/default.css'
test -z "/usr/share/beagle/webinterface/images" || /bin/mkdir -p "/usr/share/beagle/webinterface/images"
 /usr/bin/install -c -m 644 './webinterface/images/beagle-logo.png' '/usr/share/beagle/webinterface/images/beagle-logo.png'
 /usr/bin/install -c -m 644 './webinterface/images/busy-animation.gif' '/usr/share/beagle/webinterface/images/busy-animation.gif'
 /usr/bin/install -c -m 644 './webinterface/images/favicon.png' '/usr/share/beagle/webinterface/images/favicon.png'
 /usr/bin/install -c -m 644 './webinterface/images/system-search.png' '/usr/share/beagle/webinterface/images/system-search.png'
 /usr/bin/install -c -m 644 './webinterface/images/title_bg.png' '/usr/share/beagle/webinterface/images/title_bg.png'
make[2]: Leaving directory `/home/robin/beagle/beagled'
make[1]: Leaving directory `/home/robin/beagle/beagled'
Making install in Filters
make[1]: Entering directory `/home/robin/beagle/Filters'
make[2]: Entering directory `/home/robin/beagle/Filters'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/lib/beagle/Filters
mkdir -p -- /usr/lib/beagle/Filters
/usr/bin/install -c -m 644 Filters.dll Filters.dll.mdb /usr/lib/beagle/Filters
make[2]: Leaving directory `/home/robin/beagle/Filters'
make[1]: Leaving directory `/home/robin/beagle/Filters'
Making install in doc
make[1]: Entering directory `/home/robin/beagle/doc'
Making install in api
make[2]: Entering directory `/home/robin/beagle/doc/api'
make[3]: Entering directory `/home/robin/beagle/doc/api'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/monodoc/sources" || /bin/mkdir -p "/usr/lib/monodoc/sources"
 /usr/bin/install -c -m 644 'beagle-docs.zip' '/usr/lib/monodoc/sources/beagle-docs.zip'
 /usr/bin/install -c -m 644 'beagle-docs.tree' '/usr/lib/monodoc/sources/beagle-docs.tree'
 /usr/bin/install -c -m 644 'beagle-docs.source' '/usr/lib/monodoc/sources/beagle-docs.source'
make[3]: Leaving directory `/home/robin/beagle/doc/api'
make[2]: Leaving directory `/home/robin/beagle/doc/api'
make[2]: Entering directory `/home/robin/beagle/doc'
make[3]: Entering directory `/home/robin/beagle/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/robin/beagle/doc'
make[2]: Leaving directory `/home/robin/beagle/doc'
make[1]: Leaving directory `/home/robin/beagle/doc'
Making install in po
make[1]: Entering directory `/home/robin/beagle/po'
/bin/sh /home/robin/beagle/install-sh -d /usr/share/locale
linguas="ar bg ca cs da de dz el en_CA en_GB es eu fi fr gl he hi hu it ja ka ko lt lv mk nb nl oc pa pl pt_BR pt ru sl sr@Latn sr sv th tr uk vi zh_CN zh_HK zh_TW "; \
        for lang in $linguas; do \
          dir=/usr/share/locale/$lang/LC_MESSAGES; \
          /bin/sh /home/robin/beagle/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/beagle.mo; \
            echo "installing $lang.gmo as $dir/beagle.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/beagle.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/beagle.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/beagle.mo.m; \
            echo "installing $lang.gmo.m as $dir/beagle.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/beagle.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/beagle.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
installing ar.gmo as /usr/share/locale/ar/LC_MESSAGES/beagle.mo
installing bg.gmo as /usr/share/locale/bg/LC_MESSAGES/beagle.mo
installing ca.gmo as /usr/share/locale/ca/LC_MESSAGES/beagle.mo
installing cs.gmo as /usr/share/locale/cs/LC_MESSAGES/beagle.mo
installing da.gmo as /usr/share/locale/da/LC_MESSAGES/beagle.mo
installing de.gmo as /usr/share/locale/de/LC_MESSAGES/beagle.mo
installing dz.gmo as /usr/share/locale/dz/LC_MESSAGES/beagle.mo
installing el.gmo as /usr/share/locale/el/LC_MESSAGES/beagle.mo
installing en_CA.gmo as /usr/share/locale/en_CA/LC_MESSAGES/beagle.mo
installing en_GB.gmo as /usr/share/locale/en_GB/LC_MESSAGES/beagle.mo
installing es.gmo as /usr/share/locale/es/LC_MESSAGES/beagle.mo
installing eu.gmo as /usr/share/locale/eu/LC_MESSAGES/beagle.mo
installing fi.gmo as /usr/share/locale/fi/LC_MESSAGES/beagle.mo
installing fr.gmo as /usr/share/locale/fr/LC_MESSAGES/beagle.mo
installing gl.gmo as /usr/share/locale/gl/LC_MESSAGES/beagle.mo
installing he.gmo as /usr/share/locale/he/LC_MESSAGES/beagle.mo
installing hi.gmo as /usr/share/locale/hi/LC_MESSAGES/beagle.mo
installing hu.gmo as /usr/share/locale/hu/LC_MESSAGES/beagle.mo
installing it.gmo as /usr/share/locale/it/LC_MESSAGES/beagle.mo
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/beagle.mo
installing ka.gmo as /usr/share/locale/ka/LC_MESSAGES/beagle.mo
installing ko.gmo as /usr/share/locale/ko/LC_MESSAGES/beagle.mo
installing lt.gmo as /usr/share/locale/lt/LC_MESSAGES/beagle.mo
installing lv.gmo as /usr/share/locale/lv/LC_MESSAGES/beagle.mo
installing mk.gmo as /usr/share/locale/mk/LC_MESSAGES/beagle.mo
installing nb.gmo as /usr/share/locale/nb/LC_MESSAGES/beagle.mo
installing nl.gmo as /usr/share/locale/nl/LC_MESSAGES/beagle.mo
installing oc.gmo as /usr/share/locale/oc/LC_MESSAGES/beagle.mo
installing pa.gmo as /usr/share/locale/pa/LC_MESSAGES/beagle.mo
installing pl.gmo as /usr/share/locale/pl/LC_MESSAGES/beagle.mo
installing pt_BR.gmo as /usr/share/locale/pt_BR/LC_MESSAGES/beagle.mo
installing pt.gmo as /usr/share/locale/pt/LC_MESSAGES/beagle.mo
installing ru.gmo as /usr/share/locale/ru/LC_MESSAGES/beagle.mo
installing sl.gmo as /usr/share/locale/sl/LC_MESSAGES/beagle.mo
installing sr@Latn.gmo as /usr/share/locale/sr@Latn/LC_MESSAGES/beagle.mo
installing sr.gmo as /usr/share/locale/sr/LC_MESSAGES/beagle.mo
installing sv.gmo as /usr/share/locale/sv/LC_MESSAGES/beagle.mo
installing th.gmo as /usr/share/locale/th/LC_MESSAGES/beagle.mo
installing tr.gmo as /usr/share/locale/tr/LC_MESSAGES/beagle.mo
installing uk.gmo as /usr/share/locale/uk/LC_MESSAGES/beagle.mo
installing vi.gmo as /usr/share/locale/vi/LC_MESSAGES/beagle.mo
installing zh_CN.gmo as /usr/share/locale/zh_CN/LC_MESSAGES/beagle.mo
installing zh_HK.gmo as /usr/share/locale/zh_HK/LC_MESSAGES/beagle.mo
installing zh_TW.gmo as /usr/share/locale/zh_TW/LC_MESSAGES/beagle.mo
make[1]: Leaving directory `/home/robin/beagle/po'
Making install in search
make[1]: Entering directory `/home/robin/beagle/search'
make[2]: Entering directory `/home/robin/beagle/search'
test -z "/usr/lib/beagle" || /bin/mkdir -p "/usr/lib/beagle"
 /usr/bin/install -c -m 644 'Beagle.Search.exe' '/usr/lib/beagle/Beagle.Search.exe'
 /usr/bin/install -c -m 644 'Beagle.Search.exe.mdb' '/usr/lib/beagle/Beagle.Search.exe.mdb'
test -z "/etc/xdg/autostart" || /bin/mkdir -p "/etc/xdg/autostart"
 /usr/bin/install -c -m 644 'beagle-search-autostart.desktop' '/etc/xdg/autostart/beagle-search-autostart.desktop'
/bin/bash ../mkinstalldirs /usr/bin
/usr/bin/install -c beagle-search.tmp /usr/bin/beagle-search
test -z "/usr/share/applications" || /bin/mkdir -p "/usr/share/applications"
 /usr/bin/install -c -m 644 'beagle-search.desktop' '/usr/share/applications/beagle-search.desktop'
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './beagle-search.1' '/usr/share/man/man1/beagle-search.1'
make[2]: Leaving directory `/home/robin/beagle/search'
make[1]: Leaving directory `/home/robin/beagle/search'
Making install in ImLogViewer
make[1]: Entering directory `/home/robin/beagle/ImLogViewer'
make[2]: Entering directory `/home/robin/beagle/ImLogViewer'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/bin
/bin/bash ../mkinstalldirs /usr/lib/beagle
/usr/bin/install -c -m 644 ImLogViewer.exe ImLogViewer.exe.mdb /usr/lib/beagle
sed -e "s|\#installed=1|installed=1|" < beagle-imlogviewer > beagle-imlogviewer.tmp
/usr/bin/install -c beagle-imlogviewer.tmp /usr/bin/beagle-imlogviewer
rm -f beagle-imlogviewer.tmp
make[2]: Leaving directory `/home/robin/beagle/ImLogViewer'
make[1]: Leaving directory `/home/robin/beagle/ImLogViewer'
Making install in firefox-extension
make[1]: Entering directory `/home/robin/beagle/firefox-extension'
make[2]: Entering directory `/home/robin/beagle/firefox-extension'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/robin/beagle/firefox-extension'
make[1]: Leaving directory `/home/robin/beagle/firefox-extension'
Making install in tools
make[1]: Entering directory `/home/robin/beagle/tools'
make[2]: Entering directory `/home/robin/beagle/tools'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/lib/beagle
/usr/bin/install -c -m 644 Info.exe Shutdown.exe Query.exe StaticQuery.exe Config.exe Settings.exe  DocExtractor.exe Info.exe.mdb Shutdown.exe.mdb Query.exe.mdb StaticQuery.exe.mdb Config.exe.mdb Settings.exe.mdb DocExtractor.exe.mdb /usr/lib/beagle
/bin/bash ../mkinstalldirs /usr/bin
/usr/bin/install -c beagle-info.tmp /usr/bin/beagle-info
/usr/bin/install -c beagle-shutdown.tmp /usr/bin/beagle-shutdown
/usr/bin/install -c beagle-query.tmp /usr/bin/beagle-query
/usr/bin/install -c beagle-static-query.tmp /usr/bin/beagle-static-query
/usr/bin/install -c beagle-config.tmp /usr/bin/beagle-config
/usr/bin/install -c beagle-settings.tmp /usr/bin/beagle-settings
/usr/bin/install -c beagle-doc-extractor.tmp /usr/bin/beagle-doc-extractor
/usr/bin/install -c beagle-index-info.tmp /usr/bin/beagle-index-info
/usr/bin/install -c beagle-ping.tmp /usr/bin/beagle-ping
/usr/bin/install -c beagle-status.tmp /usr/bin/beagle-status
/bin/bash ../mkinstalldirs /etc/cron.daily
/usr/bin/install -c beagle-crawl-system /etc/cron.daily
test -z "/usr/share/applications" || /bin/mkdir -p "/usr/share/applications"
 /usr/bin/install -c -m 644 'beagle-settings.desktop' '/usr/share/applications/beagle-settings.desktop'
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './beagle-query.1' '/usr/share/man/man1/beagle-query.1'
 /usr/bin/install -c -m 644 './beagle-shutdown.1' '/usr/share/man/man1/beagle-shutdown.1'
 /usr/bin/install -c -m 644 './beagle-status.1' '/usr/share/man/man1/beagle-status.1'
 /usr/bin/install -c -m 644 './beagle-config.1' '/usr/share/man/man1/beagle-config.1'
make[2]: Leaving directory `/home/robin/beagle/tools'
make[1]: Leaving directory `/home/robin/beagle/tools'
Making install in conf-data
make[1]: Entering directory `/home/robin/beagle/conf-data'
make[2]: Entering directory `/home/robin/beagle/conf-data'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/etc/beagle" || /bin/mkdir -p "/etc/beagle"
 /usr/bin/install -c -m 644 'external-filters.xml.sample' '/etc/beagle/external-filters.xml.sample'
 /usr/bin/install -c -m 644 'query-mapping.xml' '/etc/beagle/query-mapping.xml'
test -z "/etc/beagle/crawl-rules" || /bin/mkdir -p "/etc/beagle/crawl-rules"
 /usr/bin/install -c -m 644 './crawl-rules/crawl-applications' '/etc/beagle/crawl-rules/crawl-applications'
 /usr/bin/install -c -m 644 './crawl-rules/crawl-documentation' '/etc/beagle/crawl-rules/crawl-documentation'
 /usr/bin/install -c -m 644 './crawl-rules/crawl-manpages' '/etc/beagle/crawl-rules/crawl-manpages'
 /usr/bin/install -c -m 644 './crawl-rules/crawl-monodoc' '/etc/beagle/crawl-rules/crawl-monodoc'
 /usr/bin/install -c -m 644 './crawl-rules/crawl-windows' '/etc/beagle/crawl-rules/crawl-windows'
test -z "/etc/beagle/config-files" || /bin/mkdir -p "/etc/beagle/config-files"
 /usr/bin/install -c -m 644 './config-files/BeagleSearch.xml' '/etc/beagle/config-files/BeagleSearch.xml'
 /usr/bin/install -c -m 644 './config-files/Daemon.xml' '/etc/beagle/config-files/Daemon.xml'
 /usr/bin/install -c -m 644 './config-files/FilesQueryable.xml' '/etc/beagle/config-files/FilesQueryable.xml'
 /usr/bin/install -c -m 644 './config-files/Networking.xml' '/etc/beagle/config-files/Networking.xml'
make[2]: Leaving directory `/home/robin/beagle/conf-data'
make[1]: Leaving directory `/home/robin/beagle/conf-data'
Making install in thunderbird-extension
make[1]: Entering directory `/home/robin/beagle/thunderbird-extension'
make[2]: Entering directory `/home/robin/beagle/thunderbird-extension'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/robin/beagle/thunderbird-extension'
make[1]: Leaving directory `/home/robin/beagle/thunderbird-extension'
make[1]: Entering directory `/home/robin/beagle'
make[2]: Entering directory `/home/robin/beagle'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/pkgconfig" || /bin/mkdir -p "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'beagle-0.0.pc' '/usr/lib/pkgconfig/beagle-0.0.pc'
 /usr/bin/install -c -m 644 'beagle-daemon.pc' '/usr/lib/pkgconfig/beagle-daemon.pc'
 /usr/bin/install -c -m 644 'beagle-ui-0.0.pc' '/usr/lib/pkgconfig/beagle-ui-0.0.pc'
make[2]: Leaving directory `/home/robin/beagle'
make[1]: Leaving directory `/home/robin/beagle'
robin@robin:~/beagle$ beagled
robin@robin:~/beagle$ 


```

---

### Post by dbera on 2008-03-25
From a terminal, run "$ beagle-ping" - see if you get any response back.

By default beagled runs in the background, whatever you pasted seems normal to me. Probably beagled is just running in the background. To start beagle-search, do
$ beagle-search

To shutdown beagle, do $ beagle-shutdown
To start beagle in the foreground, do $ beagled --fg
then you can monitor what it is doing

---

### Post by Robbyx on 2008-03-25
I realise this whole installation is exhausting for both of us but can you please suggest what I do about the following:

> robin@robin:~$ beagle-search

** (/usr/lib/beagle/Beagle.Search.exe:23107): WARNING **: Missing method NDesk.DBus.Connection::Register(ObjectPath,object) in assembly /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.dll, referenced in assembly /usr/lib/beagle/Beagle.Search.exe

Unhandled Exception: System.MissingMethodException: Method not found: 'NDesk.DBus.Connection.Register'.
robin@robin:~$ 


---

### Post by dbera on 2008-03-25
> **Robbyx said:**
> I realise this whole installation is exhausting for both of us but can you please suggest what I do about the following:

I am not least bit exhausted but I feel bad for you.

If you are using 0.3.4, then I think I know the problem, it was also reported in the beagle mailing list. Download the file
[http://svn.gnome.org/svn/beagle/trunk/beagle/search/Beagle.Search/Driver.cs](http://svn.gnome.org/svn/beagle/trunk/beagle/search/Beagle.Search/Driver.cs)
and replace beagle-0.3.4/search/Beagle.Search/Driver.cs with the downloaded one. Rebuild and re-install. It should work.

---

### Post by Robbyx on 2008-03-26
I can keep going as well. It is a bit tedious but my bigger concern is suddenly no one answers my postings. 

I replaced the driver.cs and did nothing other than the beagle-search. I am still getting error messages. Should I have done some thing extra?

> robin@robin:~$ beagle-search

** (/usr/lib/beagle/Beagle.Search.exe:7469): WARNING **: Missing method NDesk.DBus.Connection::Register(ObjectPath,object) in assembly /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.dll, referenced in assembly /usr/lib/beagle/Beagle.Search.exe

Unhandled Exception: System.MissingMethodException: Method not found: 'NDesk.DBus.Connection.Register'.
robin@robin:~$ 


---

### Post by dbera on 2008-03-26
> **Robbyx said:**
> I can keep going as well. It is a bit tedious but my bigger concern is suddenly no one answers my postings. 

I replaced the driver.cs and did nothing other than the beagle-search. I am still getting error messages. Should I have done some thing extra?

I think you forgot to install. Do this to test,
$ cd /tmp/beagle
$ cd search
$ grep Register Beagle.Search/*.cs
What does it output ? It should show the method Register() called with 3 parameters if you replaced it right.
$ make
Then run beagle-search uninstalled
$ ./beagle-search
This should run

---

### Post by Robbyx on 2008-03-26
It is working. Two things flow:
1. Following the make command this error message arose:

> ./Beagle.Search/Driver.cs(127,37): warning CS0618: `NDesk.DBus.Connection.Register(string, NDesk.DBus.ObjectPath, object)' is obsolete: `Use the overload of Register() which does not take a bus_name parameter'
Compilation succeeded - 1 warning(s)


2. I have an existing search icon in the panel that has the following properties:
Name: search
Command beagle-search

> robin@robin:~$ whereis beagle-search
beagle-search: /usr/bin/beagle-search /usr/share/man/man1/beagle-search.1
robin@robin:~$ 


I   tried setting up beagle-search by pointing it to  /usr/bin/beagle-search. Clicking on the icon does not open anything.
Can you suggest a change in syntax?

Thanks for getting me this far

Robin

---

### Post by dbera on 2008-03-26
> **Robbyx said:**
> It is working. Two things flow:
1. Following the make command this error message arose:


Ignore this.

> 
2. I have an existing search icon in the panel that has the following properties:
Name: search
Command beagle-search

I   tried setting up beagle-search by pointing it to  /usr/bin/beagle-search. Clicking on the icon does not open anything.
Can you suggest a change in syntax?


I did not understand. In any case, to get the icon in the panel you have to start beagle-search as "beagle-search --icon" (saying this from memory, I am not a gnome/beagle-search user). And /usr/bin/beagle-search is where beagle-search should be installed to.

---

### Post by Robbyx on 2008-03-27
Beagle is only working after I redo the make. The next time I try to run beagle it does not work again. Here is the terminal comments showing two attempts at running beagle:

> robin@robin:/usr/bin$ beagle-search

** (/usr/lib/beagle/Beagle.Search.exe:7224): WARNING **: Missing method NDesk.DBus.Connection::Register(ObjectPath,object) in assembly /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.dll, referenced in assembly /usr/lib/beagle/Beagle.Search.exe

Unhandled Exception: System.MissingMethodException: Method not found: 'NDesk.DBus.Connection.Register'.
robin@robin:/usr/bin$ ./beagle-search

** (/usr/lib/beagle/Beagle.Search.exe:7229): WARNING **: Missing method NDesk.DBus.Connection::Register(ObjectPath,object) in assembly /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.dll, referenced in assembly /usr/lib/beagle/Beagle.Search.exe

Unhandled Exception: System.MissingMethodException: Method not found: 'NDesk.DBus.Connection.Register'.
robin@robin:/usr/bin$ 


I hope you can help

Robin

---

### Post by dbera on 2008-03-27
> **Robbyx said:**
> Beagle is only working after I redo the make. The next time I try to run beagle it does not work again. Here is the terminal comments showing two attempts at running beagle:


Somehow your make install is not working correctly. Can you post the output of make install ? (it will be large)

---

### Post by Robbyx on 2008-03-27
I have not redone the make and the ealier steps. I have only  done the following in response to your email:

```
robin@robin:~/beagle$ sudo make install
[sudo] password for robin:
Making install in Util
make[1]: Entering directory `/home/robin/beagle/Util'
make[2]: Entering directory `/home/robin/beagle/Util'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/lib/beagle
/usr/bin/install -c -m 644 Util.dll Util.dll.mdb Util.dll.config /usr/lib/beagle
/usr/bin/install -c -m 644 UiUtil.dll UiUtil.dll.mdb ./UiUtil.dll.config /usr/lib/beagle
make[2]: Leaving directory `/home/robin/beagle/Util'
make[1]: Leaving directory `/home/robin/beagle/Util'
Making install in glue
make[1]: Entering directory `/home/robin/beagle/glue'
make[2]: Entering directory `/home/robin/beagle/glue'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/beagle" || /bin/mkdir -p "/usr/lib/beagle"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libbeagleglue.la' '/usr/lib/beagle/libbeagleglue.la'
/usr/bin/install -c .libs/libbeagleglue.so.0.0.0 /usr/lib/beagle/libbeagleglue.so.0.0.0
(cd /usr/lib/beagle && { ln -s -f libbeagleglue.so.0.0.0 libbeagleglue.so.0 || { rm -f libbeagleglue.so.0 && ln -s libbeagleglue.so.0.0.0 libbeagleglue.so.0; }; })
(cd /usr/lib/beagle && { ln -s -f libbeagleglue.so.0.0.0 libbeagleglue.so || { rm -f libbeagleglue.so && ln -s libbeagleglue.so.0.0.0 libbeagleglue.so; }; })
/usr/bin/install -c .libs/libbeagleglue.lai /usr/lib/beagle/libbeagleglue.la
/usr/bin/install -c .libs/libbeagleglue.a /usr/lib/beagle/libbeagleglue.a
chmod 644 /usr/lib/beagle/libbeagleglue.a
ranlib /usr/lib/beagle/libbeagleglue.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/beagle
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/beagle

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libbeagleuiglue.la' '/usr/lib/beagle/libbeagleuiglue.la'
/usr/bin/install -c .libs/libbeagleuiglue.so.0.0.0 /usr/lib/beagle/libbeagleuiglue.so.0.0.0
(cd /usr/lib/beagle && { ln -s -f libbeagleuiglue.so.0.0.0 libbeagleuiglue.so.0 || { rm -f libbeagleuiglue.so.0 && ln -s libbeagleuiglue.so.0.0.0 libbeagleuiglue.so.0; }; })
(cd /usr/lib/beagle && { ln -s -f libbeagleuiglue.so.0.0.0 libbeagleuiglue.so || { rm -f libbeagleuiglue.so && ln -s libbeagleuiglue.so.0.0.0 libbeagleuiglue.so; }; })
/usr/bin/install -c .libs/libbeagleuiglue.lai /usr/lib/beagle/libbeagleuiglue.la
/usr/bin/install -c .libs/libbeagleuiglue.a /usr/lib/beagle/libbeagleuiglue.a
chmod 644 /usr/lib/beagle/libbeagleuiglue.a
ranlib /usr/lib/beagle/libbeagleuiglue.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/beagle
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/beagle

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/robin/beagle/glue'
make[1]: Leaving directory `/home/robin/beagle/glue'
Making install in BeagleClient
make[1]: Entering directory `/home/robin/beagle/BeagleClient'
make[2]: Entering directory `/home/robin/beagle/BeagleClient'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/lib/beagle
/usr/bin/install -c -m 644 Beagle.dll Beagle.dll.mdb /usr/lib/beagle
make[2]: Leaving directory `/home/robin/beagle/BeagleClient'
make[1]: Leaving directory `/home/robin/beagle/BeagleClient'
Making install in beagled
make[1]: Entering directory `/home/robin/beagle/beagled'
make[2]: Entering directory `/home/robin/beagle/beagled'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/etc/xdg/autostart" || /bin/mkdir -p "/etc/xdg/autostart"
 /usr/bin/install -c -m 644 'beagled-autostart.desktop' '/etc/xdg/autostart/beagled-autostart.desktop'
/bin/bash ../mkinstalldirs /usr/bin
/bin/bash ../mkinstalldirs /usr/sbin
/bin/bash ../mkinstalldirs /usr/lib/beagle
/bin/bash ../mkinstalldirs /usr/share/beagle
/bin/bash ../mkinstalldirs /usr/lib/beagle/Backends
/usr/bin/install -c -m 644 EvolutionBackends.dll EvolutionBackends.dll.mdb /usr/lib/beagle/Backends
/usr/bin/install -c beagled.tmp /usr/bin/beagled
/usr/bin/install -c beagle-extract-content.tmp /usr/bin/beagle-extract-content
/usr/bin/install -c beagle-build-index.tmp /usr/sbin/beagle-build-index
/usr/bin/install -c beagle-dump-index.tmp /usr/sbin/beagle-dump-index
/usr/bin/install -c beagle-manage-index.tmp /usr/sbin/beagle-manage-index
/usr/bin/install -c beagle-master-delete-button.tmp /usr/sbin/beagle-master-delete-button
/usr/bin/install -c beagled-index-helper.tmp /usr/lib/beagle/beagled-index-helper
/usr/bin/install -c -m 644 BeagleDaemonPlugins.dll                 /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemonPlugins.dll.mdb             /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemonLib.dll             /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemonLib.dll.mdb         /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemon.exe                 /usr/lib/beagle
/usr/bin/install -c -m 644 BeagleDaemon.exe.mdb             /usr/lib/beagle
/usr/bin/install -c -m 644 ExtractContent.exe        /usr/lib/beagle
/usr/bin/install -c -m 644 ExtractContent.exe.mdb    /usr/lib/beagle
/usr/bin/install -c -m 644 IndexHelper.exe           /usr/lib/beagle
/usr/bin/install -c -m 644 IndexHelper.exe.mdb       /usr/lib/beagle
/usr/bin/install -c -m 644 BuildIndex.exe            /usr/lib/beagle
/usr/bin/install -c -m 644 BuildIndex.exe.mdb        /usr/lib/beagle
/usr/bin/install -c -m 644 DumpIndex.exe             /usr/lib/beagle
/usr/bin/install -c -m 644 DumpIndex.exe.mdb         /usr/lib/beagle
/usr/bin/install -c -m 644 ManageIndex.exe           /usr/lib/beagle
/usr/bin/install -c -m 644 ManageIndex.exe.mdb       /usr/lib/beagle
/usr/bin/install -c -m 644 ThunderbirdBackends.dll                 /usr/lib/beagle/Backends
/usr/bin/install -c -m 644 ThunderbirdBackends.dll.mdb             /usr/lib/beagle/Backends
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './beagled.1' '/usr/share/man/man1/beagled.1'
 /usr/bin/install -c -m 644 './beagle-dump-index.1' '/usr/share/man/man1/beagle-dump-index.1'
test -z "/usr/share/man/man8" || /bin/mkdir -p "/usr/share/man/man8"
 /usr/bin/install -c -m 644 './beagle-build-index.8' '/usr/share/man/man8/beagle-build-index.8'
 /usr/bin/install -c -m 644 './beagle-extract-content.8' '/usr/share/man/man8/beagle-extract-content.8'
 /usr/bin/install -c -m 644 './beagle-imlogviewer.8' '/usr/share/man/man8/beagle-imlogviewer.8'
 /usr/bin/install -c -m 644 './beagle-manage-index.8' '/usr/share/man/man8/beagle-manage-index.8'
test -z "/usr/share/beagle/webinterface" || /bin/mkdir -p "/usr/share/beagle/webinterface"
 /usr/bin/install -c -m 644 './webinterface/index.xml' '/usr/share/beagle/webinterface/index.xml'
 /usr/bin/install -c -m 644 './webinterface/default.js' '/usr/share/beagle/webinterface/default.js'
 /usr/bin/install -c -m 644 './webinterface/propname-table.js' '/usr/share/beagle/webinterface/propname-table.js'
 /usr/bin/install -c -m 644 './webinterface/help.html' '/usr/share/beagle/webinterface/help.html'
 /usr/bin/install -c -m 644 './webinterface/mappings.xml' '/usr/share/beagle/webinterface/mappings.xml'
 /usr/bin/install -c -m 644 './webinterface/opensearch.xml' '/usr/share/beagle/webinterface/opensearch.xml'
 /usr/bin/install -c -m 644 './webinterface/index.xsl' '/usr/share/beagle/webinterface/index.xsl'
 /usr/bin/install -c -m 644 './webinterface/hitresult.xsl' '/usr/share/beagle/webinterface/hitresult.xsl'
 /usr/bin/install -c -m 644 './webinterface/statusresult.xsl' '/usr/share/beagle/webinterface/statusresult.xsl'
 /usr/bin/install -c -m 644 './webinterface/default.css' '/usr/share/beagle/webinterface/default.css'
test -z "/usr/share/beagle/webinterface/images" || /bin/mkdir -p "/usr/share/beagle/webinterface/images"
 /usr/bin/install -c -m 644 './webinterface/images/beagle-logo.png' '/usr/share/beagle/webinterface/images/beagle-logo.png'
 /usr/bin/install -c -m 644 './webinterface/images/busy-animation.gif' '/usr/share/beagle/webinterface/images/busy-animation.gif'
 /usr/bin/install -c -m 644 './webinterface/images/favicon.png' '/usr/share/beagle/webinterface/images/favicon.png'
 /usr/bin/install -c -m 644 './webinterface/images/system-search.png' '/usr/share/beagle/webinterface/images/system-search.png'
 /usr/bin/install -c -m 644 './webinterface/images/title_bg.png' '/usr/share/beagle/webinterface/images/title_bg.png'
make[2]: Leaving directory `/home/robin/beagle/beagled'
make[1]: Leaving directory `/home/robin/beagle/beagled'
Making install in Filters
make[1]: Entering directory `/home/robin/beagle/Filters'
make[2]: Entering directory `/home/robin/beagle/Filters'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/lib/beagle/Filters
/usr/bin/install -c -m 644 Filters.dll Filters.dll.mdb /usr/lib/beagle/Filters
make[2]: Leaving directory `/home/robin/beagle/Filters'
make[1]: Leaving directory `/home/robin/beagle/Filters'
Making install in doc
make[1]: Entering directory `/home/robin/beagle/doc'
Making install in api
make[2]: Entering directory `/home/robin/beagle/doc/api'
make[3]: Entering directory `/home/robin/beagle/doc/api'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/monodoc/sources" || /bin/mkdir -p "/usr/lib/monodoc/sources"
 /usr/bin/install -c -m 644 'beagle-docs.zip' '/usr/lib/monodoc/sources/beagle-docs.zip'
 /usr/bin/install -c -m 644 'beagle-docs.tree' '/usr/lib/monodoc/sources/beagle-docs.tree'
 /usr/bin/install -c -m 644 'beagle-docs.source' '/usr/lib/monodoc/sources/beagle-docs.source'
make[3]: Leaving directory `/home/robin/beagle/doc/api'
make[2]: Leaving directory `/home/robin/beagle/doc/api'
make[2]: Entering directory `/home/robin/beagle/doc'
make[3]: Entering directory `/home/robin/beagle/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/robin/beagle/doc'
make[2]: Leaving directory `/home/robin/beagle/doc'
make[1]: Leaving directory `/home/robin/beagle/doc'
Making install in po
make[1]: Entering directory `/home/robin/beagle/po'
/bin/sh /home/robin/beagle/install-sh -d /usr/share/locale
linguas="ar bg ca cs da de dz el en_CA en_GB es eu fi fr gl he hi hu it ja ka ko lt lv mk nb nl oc pa pl pt_BR pt ru sl sr@Latn sr sv th tr uk vi zh_CN zh_HK zh_TW "; \
        for lang in $linguas; do \
          dir=/usr/share/locale/$lang/LC_MESSAGES; \
          /bin/sh /home/robin/beagle/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/beagle.mo; \
            echo "installing $lang.gmo as $dir/beagle.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/beagle.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/beagle.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/beagle.mo.m; \
            echo "installing $lang.gmo.m as $dir/beagle.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/beagle.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/beagle.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
installing ar.gmo as /usr/share/locale/ar/LC_MESSAGES/beagle.mo
installing bg.gmo as /usr/share/locale/bg/LC_MESSAGES/beagle.mo
installing ca.gmo as /usr/share/locale/ca/LC_MESSAGES/beagle.mo
installing cs.gmo as /usr/share/locale/cs/LC_MESSAGES/beagle.mo
installing da.gmo as /usr/share/locale/da/LC_MESSAGES/beagle.mo
installing de.gmo as /usr/share/locale/de/LC_MESSAGES/beagle.mo
installing dz.gmo as /usr/share/locale/dz/LC_MESSAGES/beagle.mo
installing el.gmo as /usr/share/locale/el/LC_MESSAGES/beagle.mo
installing en_CA.gmo as /usr/share/locale/en_CA/LC_MESSAGES/beagle.mo
installing en_GB.gmo as /usr/share/locale/en_GB/LC_MESSAGES/beagle.mo
installing es.gmo as /usr/share/locale/es/LC_MESSAGES/beagle.mo
installing eu.gmo as /usr/share/locale/eu/LC_MESSAGES/beagle.mo
installing fi.gmo as /usr/share/locale/fi/LC_MESSAGES/beagle.mo
installing fr.gmo as /usr/share/locale/fr/LC_MESSAGES/beagle.mo
installing gl.gmo as /usr/share/locale/gl/LC_MESSAGES/beagle.mo
installing he.gmo as /usr/share/locale/he/LC_MESSAGES/beagle.mo
installing hi.gmo as /usr/share/locale/hi/LC_MESSAGES/beagle.mo
installing hu.gmo as /usr/share/locale/hu/LC_MESSAGES/beagle.mo
installing it.gmo as /usr/share/locale/it/LC_MESSAGES/beagle.mo
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/beagle.mo
installing ka.gmo as /usr/share/locale/ka/LC_MESSAGES/beagle.mo
installing ko.gmo as /usr/share/locale/ko/LC_MESSAGES/beagle.mo
installing lt.gmo as /usr/share/locale/lt/LC_MESSAGES/beagle.mo
installing lv.gmo as /usr/share/locale/lv/LC_MESSAGES/beagle.mo
installing mk.gmo as /usr/share/locale/mk/LC_MESSAGES/beagle.mo
installing nb.gmo as /usr/share/locale/nb/LC_MESSAGES/beagle.mo
installing nl.gmo as /usr/share/locale/nl/LC_MESSAGES/beagle.mo
installing oc.gmo as /usr/share/locale/oc/LC_MESSAGES/beagle.mo
installing pa.gmo as /usr/share/locale/pa/LC_MESSAGES/beagle.mo
installing pl.gmo as /usr/share/locale/pl/LC_MESSAGES/beagle.mo
installing pt_BR.gmo as /usr/share/locale/pt_BR/LC_MESSAGES/beagle.mo
installing pt.gmo as /usr/share/locale/pt/LC_MESSAGES/beagle.mo
installing ru.gmo as /usr/share/locale/ru/LC_MESSAGES/beagle.mo
installing sl.gmo as /usr/share/locale/sl/LC_MESSAGES/beagle.mo
installing sr@Latn.gmo as /usr/share/locale/sr@Latn/LC_MESSAGES/beagle.mo
installing sr.gmo as /usr/share/locale/sr/LC_MESSAGES/beagle.mo
installing sv.gmo as /usr/share/locale/sv/LC_MESSAGES/beagle.mo
installing th.gmo as /usr/share/locale/th/LC_MESSAGES/beagle.mo
installing tr.gmo as /usr/share/locale/tr/LC_MESSAGES/beagle.mo
installing uk.gmo as /usr/share/locale/uk/LC_MESSAGES/beagle.mo
installing vi.gmo as /usr/share/locale/vi/LC_MESSAGES/beagle.mo
installing zh_CN.gmo as /usr/share/locale/zh_CN/LC_MESSAGES/beagle.mo
installing zh_HK.gmo as /usr/share/locale/zh_HK/LC_MESSAGES/beagle.mo
installing zh_TW.gmo as /usr/share/locale/zh_TW/LC_MESSAGES/beagle.mo
make[1]: Leaving directory `/home/robin/beagle/po'
Making install in search
make[1]: Entering directory `/home/robin/beagle/search'
make[2]: Entering directory `/home/robin/beagle/search'
test -z "/usr/lib/beagle" || /bin/mkdir -p "/usr/lib/beagle"
 /usr/bin/install -c -m 644 'Beagle.Search.exe' '/usr/lib/beagle/Beagle.Search.exe'
 /usr/bin/install -c -m 644 'Beagle.Search.exe.mdb' '/usr/lib/beagle/Beagle.Search.exe.mdb'
test -z "/etc/xdg/autostart" || /bin/mkdir -p "/etc/xdg/autostart"
 /usr/bin/install -c -m 644 'beagle-search-autostart.desktop' '/etc/xdg/autostart/beagle-search-autostart.desktop'
/bin/bash ../mkinstalldirs /usr/bin
/usr/bin/install -c beagle-search.tmp /usr/bin/beagle-search
test -z "/usr/share/applications" || /bin/mkdir -p "/usr/share/applications"
 /usr/bin/install -c -m 644 'beagle-search.desktop' '/usr/share/applications/beagle-search.desktop'
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './beagle-search.1' '/usr/share/man/man1/beagle-search.1'
make[2]: Leaving directory `/home/robin/beagle/search'
make[1]: Leaving directory `/home/robin/beagle/search'
Making install in ImLogViewer
make[1]: Entering directory `/home/robin/beagle/ImLogViewer'
make[2]: Entering directory `/home/robin/beagle/ImLogViewer'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/bin
/bin/bash ../mkinstalldirs /usr/lib/beagle
/usr/bin/install -c -m 644 ImLogViewer.exe ImLogViewer.exe.mdb /usr/lib/beagle
sed -e "s|\#installed=1|installed=1|" < beagle-imlogviewer > beagle-imlogviewer.tmp
/usr/bin/install -c beagle-imlogviewer.tmp /usr/bin/beagle-imlogviewer
rm -f beagle-imlogviewer.tmp
make[2]: Leaving directory `/home/robin/beagle/ImLogViewer'
make[1]: Leaving directory `/home/robin/beagle/ImLogViewer'
Making install in firefox-extension
make[1]: Entering directory `/home/robin/beagle/firefox-extension'
make[2]: Entering directory `/home/robin/beagle/firefox-extension'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/robin/beagle/firefox-extension'
make[1]: Leaving directory `/home/robin/beagle/firefox-extension'
Making install in tools
make[1]: Entering directory `/home/robin/beagle/tools'
make[2]: Entering directory `/home/robin/beagle/tools'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/lib/beagle
/usr/bin/install -c -m 644 Info.exe Shutdown.exe Query.exe StaticQuery.exe Config.exe Settings.exe  DocExtractor.exe Info.exe.mdb Shutdown.exe.mdb Query.exe.mdb StaticQuery.exe.mdb Config.exe.mdb Settings.exe.mdb DocExtractor.exe.mdb /usr/lib/beagle
/bin/bash ../mkinstalldirs /usr/bin
/usr/bin/install -c beagle-info.tmp /usr/bin/beagle-info
/usr/bin/install -c beagle-shutdown.tmp /usr/bin/beagle-shutdown
/usr/bin/install -c beagle-query.tmp /usr/bin/beagle-query
/usr/bin/install -c beagle-static-query.tmp /usr/bin/beagle-static-query
/usr/bin/install -c beagle-config.tmp /usr/bin/beagle-config
/usr/bin/install -c beagle-settings.tmp /usr/bin/beagle-settings
/usr/bin/install -c beagle-doc-extractor.tmp /usr/bin/beagle-doc-extractor
/usr/bin/install -c beagle-index-info.tmp /usr/bin/beagle-index-info
/usr/bin/install -c beagle-ping.tmp /usr/bin/beagle-ping
/usr/bin/install -c beagle-status.tmp /usr/bin/beagle-status
/bin/bash ../mkinstalldirs /etc/cron.daily
/usr/bin/install -c beagle-crawl-system /etc/cron.daily
test -z "/usr/share/applications" || /bin/mkdir -p "/usr/share/applications"
 /usr/bin/install -c -m 644 'beagle-settings.desktop' '/usr/share/applications/beagle-settings.desktop'
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './beagle-query.1' '/usr/share/man/man1/beagle-query.1'
 /usr/bin/install -c -m 644 './beagle-shutdown.1' '/usr/share/man/man1/beagle-shutdown.1'
 /usr/bin/install -c -m 644 './beagle-status.1' '/usr/share/man/man1/beagle-status.1'
 /usr/bin/install -c -m 644 './beagle-config.1' '/usr/share/man/man1/beagle-config.1'
make[2]: Leaving directory `/home/robin/beagle/tools'
make[1]: Leaving directory `/home/robin/beagle/tools'
Making install in conf-data
make[1]: Entering directory `/home/robin/beagle/conf-data'
make[2]: Entering directory `/home/robin/beagle/conf-data'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/etc/beagle" || /bin/mkdir -p "/etc/beagle"
 /usr/bin/install -c -m 644 'external-filters.xml.sample' '/etc/beagle/external-filters.xml.sample'
 /usr/bin/install -c -m 644 'query-mapping.xml' '/etc/beagle/query-mapping.xml'
test -z "/etc/beagle/crawl-rules" || /bin/mkdir -p "/etc/beagle/crawl-rules"
 /usr/bin/install -c -m 644 './crawl-rules/crawl-applications' '/etc/beagle/crawl-rules/crawl-applications'
 /usr/bin/install -c -m 644 './crawl-rules/crawl-documentation' '/etc/beagle/crawl-rules/crawl-documentation'
 /usr/bin/install -c -m 644 './crawl-rules/crawl-manpages' '/etc/beagle/crawl-rules/crawl-manpages'
 /usr/bin/install -c -m 644 './crawl-rules/crawl-monodoc' '/etc/beagle/crawl-rules/crawl-monodoc'
 /usr/bin/install -c -m 644 './crawl-rules/crawl-windows' '/etc/beagle/crawl-rules/crawl-windows'
test -z "/etc/beagle/config-files" || /bin/mkdir -p "/etc/beagle/config-files"
 /usr/bin/install -c -m 644 './config-files/BeagleSearch.xml' '/etc/beagle/config-files/BeagleSearch.xml'
 /usr/bin/install -c -m 644 './config-files/Daemon.xml' '/etc/beagle/config-files/Daemon.xml'
 /usr/bin/install -c -m 644 './config-files/FilesQueryable.xml' '/etc/beagle/config-files/FilesQueryable.xml'
 /usr/bin/install -c -m 644 './config-files/Networking.xml' '/etc/beagle/config-files/Networking.xml'
make[2]: Leaving directory `/home/robin/beagle/conf-data'
make[1]: Leaving directory `/home/robin/beagle/conf-data'
Making install in thunderbird-extension
make[1]: Entering directory `/home/robin/beagle/thunderbird-extension'
make[2]: Entering directory `/home/robin/beagle/thunderbird-extension'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/robin/beagle/thunderbird-extension'
make[1]: Leaving directory `/home/robin/beagle/thunderbird-extension'
make[1]: Entering directory `/home/robin/beagle'
make[2]: Entering directory `/home/robin/beagle'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/pkgconfig" || /bin/mkdir -p "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'beagle-0.0.pc' '/usr/lib/pkgconfig/beagle-0.0.pc'
 /usr/bin/install -c -m 644 'beagle-daemon.pc' '/usr/lib/pkgconfig/beagle-daemon.pc'
 /usr/bin/install -c -m 644 'beagle-ui-0.0.pc' '/usr/lib/pkgconfig/beagle-ui-0.0.pc'
make[2]: Leaving directory `/home/robin/beagle'
make[1]: Leaving directory `/home/robin/beagle'
robin@robin:~/beagle$ 

```

---

### Post by dbera on 2008-03-27
cd /home/robin/beagle/search/
make clean
make

Now can you attach/paste the contents of /tmp/beagle/search/beagle-search ? There is something fishy about your make install output.

---

### Post by Robbyx on 2008-03-27
> **dbera said:**
> cd /home/robin/beagle/search/
make clean
make

```
robin@robin:~/beagle/search$ sudo make clean
[sudo] password for robin:
test -z "Beagle.Search.exe Beagle.Search.exe.mdb beagle-search beagle-search.desktop beagle-search.desktop.in.h" || rm -f Beagle.Search.exe Beagle.Search.exe.mdb beagle-search beagle-search.desktop beagle-search.desktop.in.h
rm -rf .libs _libs
rm -f *.lo
robin@robin:~/beagle/search$ make
LC_ALL=C ../intltool-merge -d -u -c ../po/.intltool-merge-cache ../po beagle-search.desktop.in beagle-search.desktop
Found cached translation database
Merging translations into beagle-search.desktop.
/usr/bin/gmcs -debug -out:Beagle.Search.exe -target:exe  -define:ENABLE_XDG_OPEN -define:ENABLE_OPEN_WITH  -define:ENABLE_THUNDERBIRD  ./AssemblyInfo.cs ./Beagle.Search.Pages/Base.cs ./Beagle.Search.Pages/IndexInfo.cs ./Beagle.Search.Pages/NoMatch.cs ./Beagle.Search.Pages/QuickTips.cs ./Beagle.Search.Pages/RootUser.cs ./Beagle.Search.Pages/StartDaemon.cs ./Beagle.Search.Tiles/ActionMenuItem.cs ./Beagle.Search.Tiles/Application.cs ./Beagle.Search.Tiles/ArchivedFile.cs ./Beagle.Search.Tiles/Audio.cs ./Beagle.Search.Tiles/CApplet.cs ./Beagle.Search.Tiles/Calendar.cs ./Beagle.Search.Tiles/Contact.cs ./Beagle.Search.Tiles/Docbook.cs ./Beagle.Search.Tiles/File.cs ./Beagle.Search.Tiles/Folder.cs ./Beagle.Search.Tiles/HitFlavor.cs ./Beagle.Search.Tiles/IMLog.cs ./Beagle.Search.Tiles/Image.cs ./Beagle.Search.Tiles/MailAttachment.cs ./Beagle.Search.Tiles/MailMessage.cs ./Beagle.Search.Tiles/Manpage.cs ./Beagle.Search.Tiles/Note.cs ./Beagle.Search.Tiles/Presentation.cs ./Beagle.Search.Tiles/RSSFeed.cs ./Beagle.Search.Tiles/Spreadsheet.cs ./Beagle.Search.Tiles/Task.cs ./Beagle.Search.Tiles/TextDocument.cs ./Beagle.Search.Tiles/ThumbnailFactory.cs ./Beagle.Search.Tiles/Tile.cs ./Beagle.Search.Tiles/TileAction.cs ./Beagle.Search.Tiles/TileActivator.cs ./Beagle.Search.Tiles/TileFlat.cs ./Beagle.Search.Tiles/TileGroup.cs ./Beagle.Search.Tiles/TileTemplate.cs ./Beagle.Search.Tiles/Utils.cs ./Beagle.Search.Tiles/Video.cs ./Beagle.Search.Tiles/WebHistory.cs ./Beagle.Search.Tray/NotificationArea.cs ./Beagle.Search.Tray/TrayIcon.cs ./Beagle.Search/CairoFu.cs ./Beagle.Search/Category.cs ./Beagle.Search/DetailsPane.cs ./Beagle.Search/Driver.cs ./Beagle.Search/Entry.cs ./Beagle.Search/GroupView.cs ./Beagle.Search/ISearch.cs ./Beagle.Search/ListCategory.cs ./Beagle.Search/NotificationArea.cs ./Beagle.Search/Panes.cs ./Beagle.Search/Search.cs ./Beagle.Search/SearchWindow.cs ./Beagle.Search/SortedTileList.cs ./Beagle.Search/Spinner.cs ./Beagle.Search/TileCategory.cs ./Beagle.Search/TypeFilter.cs ./Beagle.Search/UIManager.cs ./Beagle.Search/WidgetFu.cs ./Beagle.Search.Tiles/OpenWithMenu.cs -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gconf-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gconf-sharp-peditors.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/art-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glade-sharp.dll -r:/usr/lib/cli/gmime-sharp-2.2/gmime-sharp.dll   -r:../Util/Util.dll -r:../Util/UiUtil.dll -r:../BeagleClient/Beagle.dll -r:/usr/local/lib/mono/ndesk-dbus-1.0/NDesk.DBus.dll   -r:/usr/local/lib/mono/ndesk-dbus-1.0/NDesk.DBus.dll -r:/usr/lib/cli/ndesk-dbus-glib-1.0/NDesk.DBus.GLib.dll   -r:Mono.Posix -r:Mono.Cairo
./Beagle.Search/Driver.cs(127,37): warning CS0618: `NDesk.DBus.Connection.Register(string, NDesk.DBus.ObjectPath, object)' is obsolete: `Use the overload of Register() which does not take a bus_name parameter'
Compilation succeeded - 1 warning(s)
sed                                     \
        -e "s:@pkglibdir@:/usr/lib/beagle:"     \
        -e "s:@bash@:/bin/bash:"                        \
        < ./beagle-search.in > beagle-search
chmod a+x beagle-search
robin@robin:~/beagle/search$ 

```

Now can you attach/paste the contents of /tmp/beagle/search/beagle-search ? There is something fishy about your make install output.


```
#!/bin/bash

# This line will be automatically uncommented when you "make install"
#installed=1

if [ -z $installed ] ; then
    echo "*** Running uninstalled beagle-search ***"
    THIS_EXE="./Beagle.Search.exe"

    export LD_LIBRARY_PATH="../glue/.libs${LD_LIBRARY_PATH+:$LD_LIBRARY_PATH}"
    export MONO_PATH="../Util:../BeagleClient${MONO_PATH+:MONO_PATH}"
else
    THIS_EXE="/usr/lib/beagle/Beagle.Search.exe"

    export LD_LIBRARY_PATH="/usr/lib/beagle${LD_LIBRARY_PATH+:$LD_LIBRARY_PATH}"
fi

if [ -z "$BEAGLE_MONO_RUNTIME" ]; then
   export BEAGLE_MONO_RUNTIME="mono"
else
   echo "*** Using mono runtime at $BEAGLE_MONO_RUNTIME ***"
fi

exec -a beagle-search $BEAGLE_MONO_RUNTIME $MONO_EXTRA_ARGS $THIS_EXE "$@"
```

Robin

---

### Post by dbera on 2008-03-27
This looks ok. Just confirm that
$ cd ~/beagle/search
$ ./beagle-search
works.

Now run "make install" from the search/ directory and paste the output. Sorry for asking for such details, something is not working correctly. See if it works; if it does not and gives the previous errror, paste the output of the 2 files /usr/lib/pkgconfig/ndesk*.pc

---

### Post by Robbyx on 2008-03-27
> **dbera said:**
> This looks ok. Just confirm that
$ cd ~/beagle/search
$ ./beagle-search
works.

Yes it works here is the output:
```
robin@robin:~/beagle/search$ ./beagle-search
*** Running uninstalled beagle-search ***
Debug: Done reading conf from /home/robin/.beagle/config/BeagleSearch.xml
Debug: Done reading conf from /etc/beagle/config-files/BeagleSearch.xml
Debug: Done reading conf from /home/robin/.beagle/config/Daemon.xml
Debug: Done reading conf from /etc/beagle/config-files/Daemon.xml
robin@robin:~/beagle/search$ 

```
Now run "make install" from the search/ directory and paste the output. Sorry for asking for such details, something is not working correctly. See if it works; if it does not and gives the previous errror, paste the output of the 2 files /usr/lib/pkgconfig/ndesk*.pc

```
robin@robin:~/beagle/search$ sudo make install
[sudo] password for robin:
make[1]: Entering directory `/home/robin/beagle/search'
test -z "/usr/lib/beagle" || /bin/mkdir -p "/usr/lib/beagle"
 /usr/bin/install -c -m 644 'Beagle.Search.exe' '/usr/lib/beagle/Beagle.Search.exe'
 /usr/bin/install -c -m 644 'Beagle.Search.exe.mdb' '/usr/lib/beagle/Beagle.Search.exe.mdb'
test -z "/etc/xdg/autostart" || /bin/mkdir -p "/etc/xdg/autostart"
 /usr/bin/install -c -m 644 'beagle-search-autostart.desktop' '/etc/xdg/autostart/beagle-search-autostart.desktop'
/bin/bash ../mkinstalldirs /usr/bin
/usr/bin/install -c beagle-search.tmp /usr/bin/beagle-search
test -z "/usr/share/applications" || /bin/mkdir -p "/usr/share/applications"
 /usr/bin/install -c -m 644 'beagle-search.desktop' '/usr/share/applications/beagle-search.desktop'
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './beagle-search.1' '/usr/share/man/man1/beagle-search.1'
make[1]: Leaving directory `/home/robin/beagle/search'
robin@robin:~/beagle/search$ 
```

I think it is now working as a result of the above.
I have just clicked on the search icon that runs the command

/usr/bin/beagle-search

Desktop Search loaded.

Thank you.

How can I tell if the data is actually being indexed. I found an option called index information. Everything in it marked with a 0 including the files.

Robin

---

### Post by dbera on 2008-03-27
You probably have a similar installation problem with the indexing process (known as beagled). I suggest the following:

$ beagle-shutdown
(if it says cant connect to daemon or any other error, ignore; if it hangs - reply back)

$ cd /home/robin/beagle
$ make clean
$ make
$ sudo make install

$ beagled --version
This should say beagled 0.3.4 and print the right mono version

$ beagled --fg
This command will not return the prompt and keep outputing beagled log - so do this in another terminal

now bring up beagle-search
wait for a few minutes to beagle to start indexing, then the "index information" option should start increasing. Also keep an eye on the terminal running beagled - if you see any lines with "Exception" paste those lines with 5/10 lines before and after that. If beagled gets killed, then from that terminal paste the last 10 lines beagled printed out.

To stop beagled, do a "$ beagle-shutdown" from another terminal

---

### Post by Robbyx on 2008-03-27
> **dbera said:**
> You probably have a similar installation problem with the indexing process (known as beagled). I suggest the following:

$ beagle-shutdown
(if it says cant connect to daemon or any other error, ignore; if it hangs - reply back)

$ cd /home/robin/beagle
$ make clean
$ make
$ sudo make install

$ beagled --version
This should say beagled 0.3.4 and print the right mono version

$ beagled --fg
This command will not return the prompt and keep outputing beagled log - so do this in another terminal

[COLOR="DarkOrange"]Notice the large number of attribute problems at the end:[/COLOR]
```
robin@robin:~$ beagled --fg
Always: Starting Beagle Daemon (version 0.3.4)
Always: Running on Mono 1.2.4
Always: Command Line: /usr/lib/beagle/BeagleDaemon.exe --fg
Debug: Established a connection to the X server
Debug: Reniced process to 7
Debug: Done reading conf from /home/robin/.beagle/config/Daemon.xml
Debug: Done reading conf from /etc/beagle/config-files/Daemon.xml
Debug: Starting messaging server
Debug: Done reading conf from /etc/beagle/config-files/Networking.xml
Warn: Inotify watches may be too low (8192) for some users!  Increase it to at least 65535 by setting fs.inotify.max_user_watches in /etc/sysctl.conf
Debug: Starting QueryDriver
Debug: Found index helper at /usr/lib/beagle/beagled-index-helper
Debug: Found 2 backends in /usr/lib/beagle/Backends/EvolutionBackends.dll
Debug: Found 1 backends in /usr/lib/beagle/Backends/ThunderbirdBackends.dll
Debug: Starting Inotify FSQ file event backend
Debug: Loaded 0 records from /home/robin/.beagle/Indexes/FileSystemIndex/FileAttributesStore.db in 0.000s
Debug: Done reading conf from /home/robin/.beagle/config/FilesQueryable.xml
Debug: Done reading conf from /etc/beagle/config-files/FilesQueryable.xml
Debug: KMail folders not found. Will keep trying 
Debug: KonqCacheDir: /var/tmp/kdecache-robin/http
Debug: Found 20 backends in /usr/lib/beagle/BeagleDaemonLib.dll
Debug: Loading user-configured static indexes.
Debug: Found 0 user-configured static indexes..
Debug: Waiting 60 seconds before starting queryables
Debug: Starting Scheduler thread
Debug: Starting Inotify threads
Debug: Daemon initialization finished after 1.13s
Debug: Memory usage: VmSize=66.5 MB, VmRSS=26.5 MB,  GC.GetTotalMemory=1318912 (18 colls)
Debug: Sending indexing status change from NotRunning to Running
Debug: Done reading conf from /home/robin/.beagle/config/FilesQueryable.xml
Debug: Done reading conf from /etc/beagle/config-files/FilesQueryable.xml
Debug: Starting queryables
Debug: Starting backend: 'Blam'
Debug: Starting backend: 'Thunderbird'
Debug: Starting backend: 'KonqBookmark'
Debug: Starting Thunderbird backend
Debug: No Thunderbird data to index in /home/robin/.beagle/Indexes/ThunderbirdIndex/ToIndex
Debug: Starting backend: 'KOrganizer'
Debug: Starting backend: 'Liferea'
Debug: Starting backend: 'Pidgin'
Debug: Watching for creation of Liferea directory
Debug: Starting backend: 'Tomboy'
Debug: Starting backend: 'Opera'
Debug: Starting backend: 'NetworkServices'
Debug: Starting backend: 'KAddressBook'
Debug: Tomboy backend started
Debug: Delaying backend 'NautilusMetadata' until after backend 'Files'
Debug: Starting backend: 'IndexingService'
Debug: Starting backend: 'EvolutionDataServer'
Debug: Starting backend: 'Labyrinth'
Debug: Setting up an initial crawl of the IndexingService directory
Debug: Starting backend: 'Kopete'
Debug: Starting backend: 'KNotes'
Debug: Starting backend: 'Konversation'
Debug: Starting backend: 'KMail'
Debug: Starting backend: 'Empathy'
Debug: Starting KMail backend
Debug: Starting backend: 'Akregator'
Debug: KMail directories (local mail) /home/robin/.kde/share/apps/kmail/dimap not found, will repoll.
Debug: Starting backend: 'EvolutionMail'
Debug: Starting backend: 'Files'
Debug: Starting Evolution mail backend
Debug: Adding root: /media/sda1
Error: Can't add directory: '/media/sda1' does not exist
Debug: Adding root: /media/f/Thunderbird profiles/Profiles/x8thazak.Rob/Mail
Error: Can't add directory: '/media/f/Thunderbird profiles/Profiles/x8thazak.Rob/Mail' does not exist
Debug: Done starting FileSystemQueryable
Debug: Starting backend: 'KonquerorHistory'
Debug: Starting backend: 'NautilusMetadata'
Debug: Opening bookmark file: /home/robin/.kde/share/apps/konqueror/bookmarks.xml
Debug: Checking if /home/robin/.kde/share/apps/kabc/std.vcf is a valid Kabc file.
Debug: Starting Konq history backend ...
Debug: Starting mail crawl
Debug: Mail crawl finished
Debug: Evolution mail driver worker thread done in .09s
Debug: Scanning EDS sources (Addressbook, Calendars, Memos, ...)
Debug: Nautilus metadata backend started
Debug: Getting addressbook changes for file:///home/robin/.evolution/addressbook/local/system
Debug: Addressbook file:///home/robin/.evolution/addressbook/local/system: 0 added, 0 changed, 0 removed
Debug: Getting calendar changes for file:///home/robin/.evolution/calendar/local/system
Debug: Calendar file:///home/robin/.evolution/calendar/local/system: 0 added, 0 changed, 0 removed
Debug: Getting calendar changes for contacts:///
Debug: Calendar contacts:///: 0 added, 0 changed, 0 removed
Debug: Getting calendar changes for file:///home/robin/.evolution/tasks/local/system
Debug: Calendar file:///home/robin/.evolution/tasks/local/system: 0 added, 0 changed, 0 removed
Debug: Getting calendar changes for file:///home/robin/.evolution/memos/local/system
Debug: Calendar file:///home/robin/.evolution/memos/local/system: 0 added, 0 changed, 0 removed
Debug: Scanned EDS sources in .36s
Debug: Sequence complete!
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/i.realone.com_assets_rn_cms_2005_other_www_Linux_Player_Image.6824771.jpg_68535e68
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/images.real.com_pics_real_nav_logo_real.gif_48816a1e
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/images.real.com_pics_ebi_linux_button_download_realplayer.gif_734b9e42
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/images.real.com_pics_real_realcomhome_icon_bullet_cross.gif_7a75ab8d
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/images.real.com_pics_space.gif_29fff407
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/i.realone.com_assets_rn_cms_2005_other_Helix_Community_Image.6840385.gif_7e16ce5a
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/i.real.com_pics_real_linux_bkt_bot.gif_4b29aa7c
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/images.real.com_pics_real_nav_diagonal_dk_dk.gif_7781d3fd
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/i.realone.com_assets_rn_cms_2005_other_Play_popular_datatypes_icon.6824798.gif_14712407
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/images.real.com_pics_real_nav_diagonal_lt_dk.gif_72992ae0
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/i.realone.com_assets_rn_cms_2005_other_linux_new_UI_icon.6824805.gif_0f0331a2
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/i.real.com_pics_real_linux_bkt_top.gif_6824cba7
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/i/i.realone.com_assets_rn_cms_2005_other_mozilla-compatible_plug-in_icon.6824802.gif_6a03c37e
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/r/www.real.com_realcom_css_images_bullet_white.gif_72e6a454
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/r/www.real.com_realcom_css_images_bullet_karot.gif_6a941419
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/r/www.real.com_realcom_js_omniture_s_code.js_2d86759b
Warn: Couldn't store file attributes for /var/tmp/kdecache-robin/http/r/www.real.com_realcom_css_images_bullet_round.gif_6e4dea0a
Debug: KonqQ: Crawling done
Debug: Sending indexing status change from NotRunning to Running

```

now bring up beagle-search
wait for a few minutes to beagle to start indexing, then the "index information" option should start increasing. Also keep an eye on the terminal running beagled - if you see any lines with "Exception" paste those lines with 5/10 lines before and after that. If beagled gets killed, then from that terminal paste the last 10 lines beagled printed out.

To stop beagled, do a "$ beagle-shutdown" from another terminal

The index information screen showed a change but only relating to one item Tomboy with 7. All the rest remained at 0 and there is no entry for files. 

Most of my files that need indexing are on /media/sda1.  I added that to the additional paths to be included.  I suspect that I have the syntax wrong but all I added was 
/media/sda1
I have some exclusions but they do not appear to be excluding all my files.

Robin

---

### Post by dbera on 2008-03-27
From the log "Error: Can't add directory: '/media/sda1' does not exist". Are you sure /media/sda1 exists ? i.e. from a terminal can you do "$ cd /media/sda1" ? Same with "/media/f/Thunderbird profiles/Profiles/x8thazak.Rob/Mail". Why did you add the last one btw ? For thunderbird indexing ? If it is the regular thunderbird profile place then the thunderbird backend and extension should do this automatically for you.

Those attribute errors are merely warnings; ignore them. BTW, what is the output of "$ mount" ?

To prevent taking over the system, beagle indexes slowly - so it will take some time (maybe 5-6 minutes before you start seeing files being indexed). BUT BUT BUT ... did you uncheck the "Index my home directory" option in beagle-settings ? Because it didnt add /home/robin to its list of indexing directory (no like like "Debug: Adding root /home/robin") ?

Steps:
1. from another terminal beagle-shutdown
2. if you manually unchecked "index home directory" then fine, otherwise double check that it is checked in beagle-settings. At the worst, paste the context of /home/robin/.beagle/config/FilesQueryable.xml
3. Restart beagled as before "beagled --fg --backend Files" - this will only index files - once that problem is fixed you can start with all the backends enabled.

---

### Post by Robbyx on 2008-03-27
> **dbera said:**
> From the log "Error: Can't add directory: '/media/sda1' does not exist". Are you sure /media/sda1 exists ? i.e. from a terminal can you do "$ cd /media/sda1" ? Same with "/media/f/Thunderbird profiles/Profiles/x8thazak.Rob/Mail". Why did you add the last one btw ? For thunderbird indexing ? If it is the regular thunderbird profile place then the thunderbird backend and extension should do this automatically for you.
[COLOR="DarkOrange"]I added the path to the profile because it is not in the home area. The prefs file points it to the new place. I assume that  I can take out the specific reference. If I leave it in I think it will double index all my emails. Am I correct?[/COLOR]

Those attribute errors are merely warnings; ignore them. BTW, what is the output of "$ mount" ?

```
robin@robin:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb2 on /home type ext3 (rw,nosuid,nodev,user_xattr)
/dev/sda1 on /media/mydocs type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/hdb5 on /media/downloads type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb6 on /media/flm type reiserfs (rw,noexec,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
robin@robin:~$ 
```


To prevent taking over the system, beagle indexes slowly - so it will take some time (maybe 5-6 minutes before you start seeing files being indexed). BUT BUT BUT ... did you uncheck the "Index my home directory" option in beagle-settings ? Because it didnt add /home/robin to its list of indexing directory (no like like "Debug: Adding root /home/robin") ?

[COLOR="DarkOrange"]I unticked the home because I think there is nothing in there I need indexing. [/COLOR]

Steps:
1. from another terminal beagle-shutdown
2. if you manually unchecked "index home directory" then fine, otherwise double check that it is checked in beagle-settings. At the worst, paste the context of /home/robin/.beagle/config/FilesQueryable.xml
```
<?xml version="1.0" encoding="utf-8"?>
<BeagleConf xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Name="FilesQueryable">
  <ListOption Name="ExcludePattern" Description="Exclude files matching these patters" Params="Pattern" Separator=",">
    <Value>http://www.pornbb.org/*</Value>
    <Value>*.avi</Value>
    <Value>/home/robin/download</Value>
    <Value>*.wmv</Value>
    <Value>*.wmv</Value>
  </ListOption>
  <ListOption Name="Roots" Description="Root directories that the file system backend will index" Params="Root" Separator=",">
    <Value>/media/sda1</Value>
    <Value>/media/f/Thunderbird profiles/Profiles/x8thazak.Rob/Mail</Value>
  </ListOption>
  <BoolOption Name="IndexHomeDir" Description="To index home directory">False</BoolOption>
</BeagleConf>
```
[COLOR="DarkOrange"]Next is to be done when you comment on the sda1[/COLOR]
3. Restart beagled as before "beagled --fg --backend Files" - this will only index files - once that problem is fixed you can start with all the backends enabled.

Robin

---

### Post by dbera on 2008-03-27
You are absolutely sure that /media/sda1 exists - right ? e.g. what is
$ stat /media/sda1

---

### Post by Robbyx on 2008-03-27
> **dbera said:**
> You are absolutely sure that /media/sda1 exists - right ? e.g. what is
$ stat /media/sda1

Thank you I had it wrong. Sda1 does exist but it is  not my data drive. It is the system drive. Sdb1 is the data drive and it is assigned to /media/mydocs. I have just removed the reference to sda1 and required sdb1 to be indexed instead. I have just started the indexing from within desktop search and I am now seeing files being indexed. (I have also removed the deliberate reference to the thunderbird profile.) Can I assume that once the indexing is switched on it will stay on?

It looks as if I have it working properly and for the help and advice your have given me I am very grateful. I hope that the synaptic repo will be updated soon so that as new versions come out it will not be necessary to go through the time consuming process that we have both experienced. I am very satisfied with the results. I hope it will help others who come after.

I chose ntfs for my docs because it  they are also accessed by Win2K. I can see that it is possible to use FS-Drive to access and write to ext3 drives. In view of the absence of extended attributes in ntfs would it be sensible in terms of cpu useage for me to  reformat the drive and copy back the current contents so that the drive becomes ext3?

Robin

Robin

---

### Post by dbera on 2008-03-27
> **Robbyx said:**
> Thank you I had it wrong. Sda1 does exist but it is  not my data drive. It is the system drive. Sdb1 is the data drive and it is assigned to /media/mydocs. I have just removed the reference to sda1 and required sdb1 to be indexed instead. I have just started the indexing from within desktop search and I am now seeing files being indexed. (I have also removed the deliberate reference to the thunderbird profile.) Can I assume that once the indexing is switched on it will stay on?

It should. If you want to have thunderbird indexing, then you have to install a "thunderbird extension" too. I have never done it - but I know it comes with the beagle tarball.

> 
It looks as if I have it working properly and for the help and advice your have given me I am very grateful. I hope that the synaptic repo will be updated soon so that as new versions come out it will not be necessary to go through the time consuming process that we have both experienced. I am very satisfied with the results. I hope it will help others who come after.

I think you are not using hardy; in that case I doubt the newer versions will be backported to whatever feisty/gutsy you are using.

> 
I chose ntfs for my docs because it  they are also accessed by Win2K. I can see that it is possible to use FS-Drive to access and write to ext3 drives. In view of the absence of extended attributes in ntfs would it be sensible in terms of cpu useage for me to  reformat the drive and copy back the current contents so that the drive becomes ext3?


If you are worried about extended attributes due to beagle, then you need not worry. Extended attribute is recommended but not neessary and beagle will work fine without it.

---

### Post by Robbyx on 2008-03-28
I realise that you have not used the thunderbird extension, but I am hoping that you or even someone else may be able to suggest a way forward based on general principles. 

I found a thunderbird xpi file in the beagle package and without adjustment or recompiling added it into Thunderbird as an addon. It now appears in the Thunderbird addons as a beagle indexer.

There are no instructions as to how to install the Thunderbird extension so I have had to guess that there is no need to make, and make install, although those files are in the TB extension folder within the beagle package.

It seems to be working with Thunderbird files showing in the index information. I had left the machine on overnight and although when the index started on TB there was a window that kept saying it was attempting to contact the host with login info I ignored it. I assume that the addon also tries to index online emails. The result appears to be my emails have been indexed,  but I am not seeing any extract of the email within the search result. I only see the subject of the email. I am used to seeing the first say 200 characters being returned as part of a search. Do you know if Beagle does this as well?

Robin

---

### Post by Robbyx on 2008-03-28
I do not know if this is an error message relating to beagle, but I have just found a whole load of error messages flaged up in the bottom right corner of Thunderbird. They all say:

An error occurred while indexing. Error description:
TypeError: account.incomingServer has no properties

Do you know what this is about?

Robin

---

### Post by Robbyx on 2008-03-28
I can now see an outline of a Beagle behind the triangle indicating the error message. Maybe this means the error messages are Beagle problems?

---

### Post by dbera on 2008-03-28
> **Robbyx said:**
> It seems to be working with Thunderbird files showing in the index information. I had left the machine on overnight and although when the index started on TB there was a window that kept saying it was attempting to contact the host with login info I ignored it. I assume that the addon also tries to index online emails. The result appears to be my emails have been indexed,  but I am not seeing any extract of the email within the search result. I only see the subject of the email. I am used to seeing the first say 200 characters being returned as part of a search. Do you know if Beagle does this as well?
Robin

Maybe it only shows the body of the email for offline (what it called, stored imap / disconnected imap ?) emails; I am guessing that for online emails, the running Thunderbird app only has the email header and so that is all that beagle indexes. Indexing the body of the email would mean fetching the body off the mail server, which is probably something beagle does not want to do.

---

### Post by dbera on 2008-03-28
> **Robbyx said:**
> I do not know if this is an error message relating to beagle, but I have just found a whole load of error messages flaged up in the bottom right corner of Thunderbird. They all say:

An error occurred while indexing. Error description:
TypeError: account.incomingServer has no properties


They are possibly beagle related errors. Can't say much :) You might want to file a bug with beagle if you feel the need.

---

### Post by Robbyx on 2008-03-28
> **dbera said:**
> Maybe it only shows the body of the email for offline (what it called, stored imap / disconnected imap ?) emails; I am guessing that for online emails, the running Thunderbird app only has the email header and so that is all that beagle indexes. Indexing the body of the email would mean fetching the body off the mail server, which is probably something beagle does not want to do.

I am not using imap. My emails are on Pop3.  Unless you come back, suggesting a change in the settings I will file a report or see if there is a specific thread for Beagle. Thank you for much for your patience and perseverance in supporting me.

Robin

---

### Post by Robbyx on 2008-04-02
At the moment I have 1100 unread warnings in Thunderbird about Beagle. They are repeats of the typeError I referred to above. Do you know how to report a bug in Beagle or do you know if there is an active forum discussing Beagle? 

I have two queries concerning Beagle. 

[LIST=1]
[*] Should I expect Beagle to report the first few lines of content of an email in Thunderbird? At present it only shows the subject line with no content.
[*] I just type trackerd to see if it was running as well as beagle. This was the response:
> Initialising tracker...

** (trackerd:9540): WARNING **: Tracker daemon is already running - exiting
robin@robin:~$ 

Does this mean I have both Tracker and Beagle running?
[/LIST]

---

### Post by dbera on 2008-04-02
> **Robbyx said:**
> At the moment I have 1100 unread warnings in Thunderbird about Beagle. They are repeats of the typeError I referred to above. Do you know how to report a bug in Beagle or do you know if there is an active forum discussing Beagle? 
[http://bugzilla.gnome.org/enter_bug.cgi?product=beagle](http://bugzilla.gnome.org/enter_bug.cgi?product=beagle)
[http://mail.gnome.org/mailman/listinfo/dashboard-hackers](http://mail.gnome.org/mailman/listinfo/dashboard-hackers)

> 
Should I expect Beagle to report the first few lines of content of an email in Thunderbird? At present it only shows the subject line with no content.
I think so.

> 
I just type trackerd to see if it was running as well as beagle. This was the response:
Does this mean I have both Tracker and Beagle running?
Looks like it.

---

### Post by dbera on 2008-04-02
> **Robbyx said:**
> I had left the machine on overnight and although when the index started on TB there was a window that kept saying it was attempting to contact the host with login info I ignored it.

What exactly did you ignore ? Could that be the reason of all the errors ?

---

### Post by Robbyx on 2008-04-02
> **dbera said:**
> What exactly did you ignore ? Could that be the reason of all the errors ?

An error occurred while indexing. Error description:
TypeError: account.incomingServer has no properties

---

### Post by dbera on 2008-04-02
> **Robbyx said:**
> An error occurred while indexing. Error description:
TypeError: account.incomingServer has no properties

No I meant > there was a window that kept saying it was attempting to contact the host with login info
Can you give more detail about this ? What exactly was it asking / informing ? What happens if you do not ignore it. If it does not ask for that information any more, maybe it only asks that at the beginning. In that case stop Thunderbird, beagle, remove ~/.beagle/Indexes/ThunderbirdIndex and then restart everything.

---

### Post by Robbyx on 2008-04-03
> **dbera said:**
> No I meant 
Can you give more detail about this ? What exactly was it asking / informing ? What happens if you do not ignore it. If it does not ask for that information any more, maybe it only asks that at the beginning. In that case stop Thunderbird, beagle, remove ~/.beagle/Indexes/ThunderbirdIndex and then restart everything.

I am not longer getting the error mesage relating to a window that kept saying it was attempting to contact the host with login info

Currently the only error message I am getting is with  a red triangle over the beagle icon in Thunderbird. When  I click on it an alert pops up with

> An error occurred while indexing. Error description:
TypeError: account.incomingServer has no properties

Apart from that when I  do a key word search,  the bottom half of the screen does not give me much information.  I can now see that what it is returning is the full path and the words surrounding the hit of the key word search. I am not sure it is returning all the hits in the doc, but is there a way of seeing more of the actual article or email in that lower box? Say the beginning couple of lines?

---

### Post by dbera on 2008-04-03
> I am not longer getting the error mesage relating to a window that kept saying it was attempting to contact the host with login info

Oh so the window was not asking for anything but only displaying some information ? I think the red-triangle error message is related to this, just a wild guess but could be true. Possibly beagle had to contact the host for some more information.

> Apart from that when I  do a key word search,  the bottom half of the screen does not give me much information.  I can now see that what it is returning is the full path and the words surrounding the hit of the key word search. I am not sure it is returning all the hits in the doc, but is there a way of seeing more of the actual article or email in that lower box? Say the beginning couple of lines


I am not sure what you are seeing. A screenshot would be helpful. But do you see, in the bottom half, parts of the lines from the email containing the matched word ?

---

### Post by Robbyx on 2008-04-03
I having a problem with desktop search screen. I had this before. It worked when  I started the computer this morning. Now the screen opens up as grey window and does not fill up with any writing or other content.

Sorry I can not work out how to send you a screen print. I saved a png to the desktop. Used the picture icon, put in the url to my desktop and the picture did not show on preview.

Robin

---

### Post by dbera on 2008-04-03
I dont want you to go through the trouble of compiling a new version of beagle but the grey window was a regression in 0.3.4; it was spotted and fixed in 0.3.5. If you are able to patch your local source, these are the changes you need:
[http://svn.gnome.org/viewvc/beagle?view=revision&revision=4649](http://svn.gnome.org/viewvc/beagle?view=revision&revision=4649)

Alternatively, restart desktop-search but DO NOT use the shortcut key, always click on the tray icon to show/hide.

---

### Post by Robbyx on 2008-04-03
Thank you for your help. In my case the grey screen is resulting from clicking on the tray icon. I have not been using a shortcut.

Robin

---

### Post by dbera on 2008-04-03
The patch might still help.

---

### Post by dbera on 2008-04-03
> In my case the grey screen is resulting from clicking on the tray icon. I have not been using a shortcut.

Actually, I meant to say "never close using the [X] window close button". Always use the tray iconn to show or hide with 0.3.4. If even that creates the grey window, then it is probably another bug.

---

### Post by dbera on 2008-04-03
And I found this for the error message you are seeing.
[http://mail.gnome.org/archives/dashboard-hackers/2007-August/msg00097.html](http://mail.gnome.org/archives/dashboard-hackers/2007-August/msg00097.html)
(follow the emails in the thread)

---

### Post by Robbyx on 2008-04-03
> **dbera said:**
> And I found this for the error message you are seeing.
[http://mail.gnome.org/archives/dashboard-hackers/2007-August/msg00097.html](http://mail.gnome.org/archives/dashboard-hackers/2007-August/msg00097.html)
(follow the emails in the thread)
Does it apply to pop3 mail? I do not use imap.

---

### Post by dbera on 2008-04-03
> **Robbyx said:**
> Does it apply to pop3 mail? I do not use imap.

I think it does, I read something like that in a message earlier in that thread.

---

### Post by Robbyx on 2008-04-03
I installed v3.5. It is currently working. I assume it will continue to do so and will not become a grey screen.

I asked you about the number of words surrounding a hit and the display of the beginning of document.  you can see it is not happening. 

[[img]http://img2.freeimagehosting.net/uploads/th.cf97461e7f.png[/img]](http://img2.freeimagehosting.net/image.php?cf97461e7f.png)

Please click on the image. It does get a bit bigger. I have also added an attachment which shows much better detail of the search screen

Robin

---

### Post by dbera on 2008-04-03
Ah ok I see what you mean. I dont know how the thunderbird backend works, so ..can you do the following:

Decide on some query words. The fewer emails it matches, the better (but should match at least 1). But choose some word for which you expect some surrounding words to be shown. Use the query words below in place of QUERY
$ beagle-query source:Thunderbird QUERY
=> this will print lots of URLs, pick any one. Copy it. Use it below in place of URI
$ beagle-query --verbose --cache uri:"URI"

Paste the output here. (Choose search words so that the email is not too personal to not post here).

---

### Post by Robbyx on 2008-04-04
> robin@robin:~$ beagle-query source:Thunderbird MBBS
Debug: Done reading conf from /home/robin/.beagle/config/Daemon.xml
Debug: Done reading conf from /etc/beagle/config-files/Daemon.xml
robin@robin:~$ beagle-query --verbose --cache uri:/etc/beagle/config-files/Daemon.xml
Debug: Done reading conf from /home/robin/.beagle/config/Daemon.xml
Debug: Done reading conf from /etc/beagle/config-files/Daemon.xml
Elapsed time: 0.172s
Total hits: 0
robin@robin:~$ beagle-query --verbose --cache uri:"/etc/beagle/config-files/Daemon.xml"
Debug: Done reading conf from /home/robin/.beagle/config/Daemon.xml
Debug: Done reading conf from /etc/beagle/config-files/Daemon.xml
Elapsed time: 0.152s
Total hits: 0
robin@robin:~$ 


It seems to me that the indexing is not complete. I beagled on MBBS and it came up with a word document rather than the email in which  I had manually found the term.

Robin

---

### Post by dbera on 2008-04-04
Err.. not the debug lines. Ignore the "Debug:" lines when choosing for URLs. MBBS for you didnot return a search result. Can you try with something else (use the search words which you used to create the screenshot) ?

---

### Post by Robbyx on 2008-04-04
I am a bit muddled. I installed 3.5 and it comes up on a search. When  I searched for a key word that  I found in a file, "Beddington" it was not found by Beagle. Should I start a new index? If so how?

I can see that on other key words that are being found only the words either side, on the same line, are being returned. Is possible to increase this to show a few lines or the beginning of the document. This seems to apply to both TB emails and saved documents.

---

### Post by dbera on 2008-04-04
> I am a bit muddled. I installed 3.5 and it comes up on a search. When  I searched for a key word that  I found in a file, "Beddington" it was not found by Beagle. Should I start a new index? If so how?
:P I could not follow you, sorry.

> 
I can see that on other key words that are being found only the words either side, on the same line, are being returned. Is possible to increase this to show a few lines or the beginning of the document. This seems to apply to both TB emails and saved documents.

No. This is a limitation of the program. You can hover your mouse over those words and sometimes that give you little bit more context but definitely not what you are looking for.

---

### Post by Robbyx on 2008-04-05
Something has gone wrong with the indexing. Words which I know are in the files are not being found. I therefore thought it would be wise to remove the current index and create a new one.

NB Program limitation noted

---

### Post by dbera on 2008-04-05
0.3.5, IIRC, will remove the old index and re-index everything from scratch. Maybe when you tried it hadnt finished reindexing yet.

If you want to create a new index,
1. stop thunderbird
2. stop beagled ($ beagle-shutdown)
3. $ rm -rf ~/.beagle/Indexes/ThunderbirdIndex
4. Restart beagled and then thunderbird

---

