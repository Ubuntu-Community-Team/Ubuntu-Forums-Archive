---
title: "Compiling problem, help!"
date: 2004-11-11
forum: General Help
---

### Post by mdweezer on 2004-11-11
Well, I expected a problem when trying to compile this application (OpenVMPS) however I didn't expect this big of a problem!!!

root@CITA230Lab:/home/mdweezer/vmpsd # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
root@CITA230Lab:/home/mdweezer/vmpsd #

This is just a basic Ubuntu install, I didn't change or update anything, are no development tools installed by default or is my $PATH wrong or something?

Thanks in advance!

---

### Post by mdweezer on 2004-11-11
Sorry for your troubles, found the FAQ and install the essential build tools!!!!

Thanks :)

---

### Post by ashley_v on 2004-11-11
[QUOTE=][/QUOTE]
 According to that and my use of compiling software here is what you need.

apt-get update && apt-get install gcc g++ gawk 

I doubt gawk is needed but the gnu c and c++ compilers you'll surely need to compile just about anything from source.

---

### Post by WW on 2004-11-11
ashley_v:

I think mdweezer was saying that s/he found the **build-essential** package.  This is a meta-package that will install all the basic C/C++ tools (gcc, g++, etc).

---

### Post by ashley_v on 2004-11-11
[QUOTE=][/QUOTE]
 Compiling a standalone application and building a debian package are two different things.  My understanding of the essential-build package is for building debian packages.  Not compiling something with traditional method of:

./configure ; make ; make install ; make clean

For that all you need is gcc and maybe g++.  There are other components of gcc like objective c, java, and fortran compilers but their not required as much.  So if your never planning on building .deb packages why use the build-essential package?

---

### Post by WW on 2004-11-11
Good question.  I poked around in Synaptic to try to find an
answer.

Synaptic tells me that the build-essential package depends on
libc6-dev or libc-dev, g++, gcc, make, and dpkg-dev.  If you are
not building deb packages, then you probably don't need dpkg-dev.
It appears to this non-guru that an alternative to installing
build-essential is

   apt-get install libc6-dev g++ gcc make

Installing build-essential will also install an assortment of files in
/usr/share that you will probably never read (well, I never
have).  Synaptic tells me that dpkg-dev depends on perl5,
perl-modules, cpio, patch, make and binutils.  If these are not
already installed when build-essential is installed, they will also
be installed. (That's as far as I bothered tracing back the 
dependency tree.)  So the dpkg-dev dependency in build-essential
might result in several more packages being installed than
you really need.

It appears to me that using the apt-get command above
will save a bit of download time and disk space.  But frankly,
when someone asks about compiling programs, I find it much
easier to tell them to install build-essential!

WW

---

### Post by mdweezer on 2004-11-11
I hope this helps settle all of this :)

Once I installed the build-essentials package I was able to successfully ./configure, make, and make install the application I was trying to compile....  Worked flawlessly.   \\:D/ 

Enjoy!

---

### Post by ashley_v on 2004-11-11
[QUOTE=][/QUOTE]
 If you all choose to install thoose tools just to build from source then at least be a good sport and make true use of the build-essentials package.  What I mean is if your going to use it then go ahead and make a debian package for your fellow debian users so we won't have to build from source.  Good luck getting them into a repository or heak create your on repository with all the apps you have installed that are not already in the repository.

Other than that, for future references if your not using debian or a debian based system like Ubuntu here is what you will generally need to compile something from source.

autoconf
automake
make
gawk
gcc
g++

Once again the build-essentials package is only for building .deb packages.  It's your choice if you want to install it but I take it most of you will learn how to build your own .deb packages sooner or later so it's a good learning edge.

---

