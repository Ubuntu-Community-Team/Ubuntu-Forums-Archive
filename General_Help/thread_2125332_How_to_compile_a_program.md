---
title: "How to compile a program?"
date: 2013-03-13
forum: General Help
---

### Post by Kols on 2013-03-13
Hi!

When ever I google how to compile a program, this is the instruction

```
tar xvjf file.bz2
cd file
./configure
make
su
make install
```

...which seems nice and dandy. However, when EVER I do it, this happens

```
~/System/PDFedit/pdfedit-0.4.5 $ ./configure
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether the C++ compiler works... no
configure: error: in `/home/ojkolsrud/System/PDFedit/pdfedit-0.4.5':
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
```

I'm always missing a lot of dependencies or something. Now, I just installed g++ from the magical apt-get, and output now looks like this:
```

~/System/PDFedit/pdfedit-0.4.5 $ ./configure
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether make sets $(MAKE)... yes
checking for ranlib... ranlib
checking whether ln -s works... yes
checking how to run the C++ preprocessor... g++ -E
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
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking how to run the C preprocessor... gcc -E
checking if zlib is wanted... checking for inflateEnd in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for inflateEnd in -lz... (cached) yes
checking zlib in /usr... ok
checking for boostlib >= 1.20.0... configure: error: We could not detect the boost libraries (version 1.20 or higher). If you have a staged boost library (still not installed) please specify $BOOST_ROOT in your environment and do not give a PATH to --with-boost option.  If you are sure you have boost installed, then check your version number looking in <boost/version.hpp>. See http://randspringer.de/boost for more documentation.
```

Now, Boost isn't a program i can fetch from apt-get. I could do a ```
find | grep -i 'boost'
``` (yeah, it's probably a stupid way to search for files, but it works) to find it, but I rather don't. 

My question is, is there a standard compiler package that includes the most common compiler tools needed for programs like this? I'm starting to feel like a real newb when I always have to google for package.deb or look for PACKAGE FOR UBUNTU-USERS.

Sorry about raging=P

cheers!

---

### Post by MG&amp;TL on 2013-03-13
To answer your problem: according to [https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit), *pdfedit* has been in the repositories since 7.10. Do you have a good reason to be compiling it?

To answer your question: no, not really. The *build-essential* package contains most of the generic packages like the C and C++ compilers, the development C libraries and such, but most programs will use some other libraries, like *boost* (which, as a matter of interest, is a general-purpose C++ library, quite a few projects use it). I believe you want the *libboost-dev* package.

---

### Post by schragge on 2013-03-13
> **Kols said:**
> Now, Boost isn't a program i can fetch from apt-get.```
sudo apt-get install libboost-all-dev
```

> **Kols said:**
> My question is, is there a standard compiler package that includes the most common compiler tools needed for programs like this?```
sudo apt-get install build-essential
```

---

### Post by Kols on 2013-03-13
> **MG&TL said:**
> To answer your problem: according to [https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit), *pdfedit* has been in the repositories since 7.10. Do you have a good reason to be compiling it?

To answer your question: no, not really. The *build-essential* package contains most of the generic packages like the C and C++ compilers, the development C libraries and such, but most programs will use some other libraries, like *boost* (which, as a matter of interest, is a general-purpose C++ library, quite a few projects use it). I believe you want the *libboost-dev* package.


Thanks for answering! 

The thing is, PDFedit isn't in reps any more. I'm sure there are other, better editors, but installing that particular one isn't really the case: I want to be able to compile stuff, as many programs don't come with a handy .deb.

I just installed your suggested package, libbost-dev. This is the tail of the newest output of ./configure as of yet:

```
~/System/PDFedit/pdfedit-0.4.5 $ ./configure

configure: error: QTDIR environment variable must be set


```

I think you know what my question is=P

Also, when I compile, are the programs installed where everything else is (/etc and /bin etc), or do I have to specify that?

I'm thankful for your patiance - I've been using Linux for almost a year now. I've learnt a whole lot, and enjoyed myself just as much, but some things are still pretty murky.

Cheers again!

---

### Post by Kols on 2013-03-13
> **schragge said:**
> ```
sudo apt-get install libboost-all-dev
```

```
sudo apt-get install build-essential
```

Thanks a lot! Both are now installed.

---

### Post by Kols on 2013-03-13
> **Kols said:**
> Thanks for answering! 

The thing is, PDFedit isn't in reps any more. I'm sure there are other, better editors, but installing that particular one isn't really the case: I want to be able to compile stuff, as many programs don't come with a handy .deb.

I just installed your suggested package, libbost-dev. This is the tail of the newest output of ./configure as of yet:

```
~/System/PDFedit/pdfedit-0.4.5 $ ./configure

configure: error: QTDIR environment variable must be set


```

I think you know what my question is=P

Also, when I compile, are the programs installed where everything else is (/etc and /bin etc), or do I have to specify that?

I'm thankful for your patiance - I've been using Linux for almost a year now. I've learnt a whole lot, and enjoyed myself just as much, but some things are still pretty murky.

Cheers again!



Now, after googling a bit, I found that someone else had the exact same problem, with the same program.

They suggested the following:

```
sudo QTDIR=/usr/share/qt3 ./configure


```

Which solved their problem, but produced this on my box:


```
configure: QMAKESPEC environment variable is not set
                - default will be used.
checking for QT qmake... configure: error: unable to find qmake for QT3

```

wat...

I love Linux, but sometimes...

---

### Post by schragge on 2013-03-13
You need install all build-dependencies for pdfedit. Obviously, qmake is one of them. You also probably need
```
sudo apt-get install doxygen libpaper-dev xsltproc
``` Note that this list is not full, better check README and/or INSTALL for pdfedit. Also note that Qt3 is not in repositories for quantal anymore, and I'm not sure pdfedit will compile with Qt4.

---

### Post by ManamiVixen on 2013-03-13
[**[COLOR=#000000]schragge[/COLOR]**]("http://ubuntuforums.org/member.php?u=1783515") he also needs qt3 libraries and tools

---

### Post by schragge on 2013-03-13
@**ManamiVixen**
Yeah, have already noticed that and edited the post.

---

### Post by Kols on 2013-03-13
> **schragge said:**
> You need install all build-dependencies for pdfedit. Obviously, qmake is one of them. You also probably need
```
sudo apt-get install doxygen libpaper-dev xsltproc
``` Note that this list is not full, better check README and/or INSTALL for pdfedit. Also note that Qt3 is not in repositories for quantal anymore, and I'm not sure pdfedit will compile with Qt4.

I simulated install of those packages, and to my surprise, nearly 1 gig was needed! I'm gonna try the qmake-trick first. To answer your question regarding whether pdfedit would compile with qt4, the answer is no - it won't. 

Now, is the best approach to remove qt4, and look for a place to download qt3? Haha, with my luck, I won't be able to compile that either=P

Is it possible to run a compile process which would automatically fetch the needed packages? I'm thinking a code like this

```
./configure --[option to output output dependencies]* | apt-get install [dependencies]
```   *i know ./configure isn't a program itself, but still, to somehow append an option to it.

Thanks a lot for all your patience!

---

### Post by schragge on 2013-03-13
> **Kols said:**
> Is it possible to run a compile process which would automatically fetch the needed packages?This won't work I'm afraid. You cannot always infer the package names from *configure *output. Often, you have to search for them with [apt-file](http://manpages.ubuntu.com/manpages/precise/man1/apt-file.1.html).

---

### Post by oldos2er on 2013-03-13
Have you read the README file? There's a lot of info there on what you need to compile pdfedit. 

./configure is a program; it's a shell script that does some grunt work for you before running make.

Also see (if you haven't already) [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by steeldriver on 2013-03-13
Since pdfedit is 0.4.5 is available on 12.04 you could maybe use the build-deps from that as a starting point: 

```

$ sudo apt-get --dry-run build-dep pdfedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cdbs comerr-dev dh-translations doxygen intltool krb5-multidev libaudio-dev libboost-iostreams-dev libcups2-dev libgcrypt11-dev libgnutls-dev
  libgnutls-openssl27 libgnutlsxx27 libgpg-error-dev libgssrpc4 libjpeg-dev libjpeg-turbo8-dev libjpeg8-dev libkadm5clnt-mit8 libkadm5srv-mit8 libkdb5-6
  libkrb5-dev liblcms1-dev libmng-dev libp11-kit-dev libpaper-dev libqt3-headers libqt3-mt libqt3-mt-dev libtasn1-3-dev libxml-parser-perl python-scour
  qt3-dev-tools xsltproc
.
.
.

```

```

$ apt-cache search --names-only pdfedit
pdfedit - Editor for manipulating PDF documents
$
$ apt-cache policy pdfedit
pdfedit:
  Installed: (none)
  Candidate: 0.4.5-2
  Version table:
     0.4.5-2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
$ 

```

---

