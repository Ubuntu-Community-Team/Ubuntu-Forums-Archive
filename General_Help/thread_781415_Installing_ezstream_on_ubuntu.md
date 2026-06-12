---
title: "Installing ezstream on ubuntu"
date: 2008-05-04
forum: General Help
---

### Post by Wessel on 2008-05-04
I want to install ezstream on ubuntu, but i can't find a .deb anywhere, so I downloaded the source from

```
http://downloads.us.xiph.org/releases/ezstream/ 
```

But i don't know how to compile it, i tried sudo apt-get build-dep, but that doens't work...

How do I install ezstream?

---

### Post by ghost_ryder35 on 2008-05-04
> **Wessel said:**
> I want to install ezstream on ubuntu, but i can't find a .deb anywhere, so I downloaded the source from
 
```
http://downloads.us.xiph.org/releases/ezstream/ 
```
 
But i don't know how to compile it, i tried sudo apt-get build-dep, but that doens't work...
 
How do I install ezstream?
do you have build-essential?
```

sudo apt-get install build-essential

```
then check out 
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Wessel on 2008-05-04
It won't work, i've installed build-essential, and automake. Then i've done this:

```

cd ezstream-0.5.3
./configure
cd ../
sudo apt-get build-dep ezstream-0.5.3

```

But it doesn't work...

---

### Post by ghost_ryder35 on 2008-05-04
> **Wessel said:**
> It won't work, i've installed build-essential, and automake. Then i've done this:
 
```

cd ezstream-0.5.3
./configure
cd ../
sudo apt-get build-dep ezstream-0.5.3

```
 
But it doesn't work...
can you be more specific than "but it doesnt work"  try posting any errors that the terminal might produce

---

### Post by Wessel on 2008-05-04
I have a dutch pc, so the errors are in dutch, but i try to translate it:p

```
wessel@wessel-zpox:~$ cd /home/wessel/Bureaublad/ezstream-0.5.3
wessel@wessel-zpox:~/Bureaublad/ezstream-0.5.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for AIX... no
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether to enable debugging... no
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking whether libc defines __progname... yes
checking for an ANSI C-conforming const... yes
checking for working volatile... yes
checking for size_t... yes
checking for ssize_t... yes
checking for struct timeval... yes
checking for basename in -lgen... no
checking for arc4random... no
checking for gettimeofday... yes
checking for nl_langinfo... yes
checking for random... yes
checking for setlocale... yes
checking for srandomdev... no
checking for stat... yes
checking for getopt... yes
checking for strlcat... no
checking for strlcpy... no
checking for strtonum... no
checking for sigaction... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for fgrep... /bin/grep -F
checking for TagLib option... autodetect
checking taglib/tag_c.h usability... no
checking taglib/tag_c.h presence... no
checking for taglib/tag_c.h... no
configure: No TagLib C header found on this system
checking for libogg... ok
checking for libvorbis... not found
configure: error: Must have libvorbis 1.x installed.
wessel@wessel-zpox:~/Bureaublad/ezstream-0.5.3$ cd ../
wessel@wessel-zpox:~/Bureaublad$ sudo apt-get build-dep ezstream-0.5.3
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar
E: Kan geen bronpakket vinden voor ezstream-0.5.3
wessel@wessel-zpox:~/Bureaublad$ 

```

The error "E: Kan geen bronpakket vinden voor ezstream-0.5.3" means: "	
E: Can not find source for ezstream-0.5.3"

---

### Post by ghost_ryder35 on 2008-05-04
can you post the readme file from the ezstream tar file

---

### Post by Wessel on 2008-05-04
here, in the attachement ([http://ubuntuforums.org/attachment.php?attachmentid=68742&stc=1&d=1209905458](http://ubuntuforums.org/attachment.php?attachmentid=68742&stc=1&d=1209905458))

---

### Post by ghost_ryder35 on 2008-05-04
you have the dependencies?
[SIZE=2]Ezstream depends on:
* libshout 2.2.x ([http://www.icecast.org/](http://www.icecast.org/))
* libshout dependencies, such as libogg, libvorbis, libtheora, etc.
([http://www.vorbis.com/](http://www.vorbis.com/) and [http://www.theora.org/](http://www.theora.org/))
* libxml 2.x ([http://xmlsoft.org/](http://xmlsoft.org/))
 
#####################
[SIZE=2]The compilation and installation process boils down to the usual
$ ./configure --help | less # Skim over the available options
$ ./configure [options] && make && [sudo] make install
# Configure, build and install
# [as root] the software
If this procedure is unfamiliar to you, please consult the INSTALL file for
more detailed instructions.
 
Might want to check out that INSTALL file
[/SIZE][/SIZE]

---

### Post by Wessel on 2008-05-04
I have all that dependencies, but if I do ./configure, it says you must have libvorbis to. So i downloaded libvorbis, and i tried to install it, but then a error came up: Error: Dependecy is not satisfiable: libvorbis0a

I tried to remove libvorbis0a, but then it's going to remove ubuntu-desktop and other programs as well, so i'm not going to remove libvorbis0a. But i must have libvorbis?

---

