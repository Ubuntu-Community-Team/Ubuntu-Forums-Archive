---
title: "installing OpenJdk in Ubuntu 12.04"
date: 2013-10-24
forum: General Help
---

### Post by raffi_1970 on 2013-10-24
Folks,

I'm having a hell of a time installing OpenJDK in Ubuntu 12.04, or more accurately completing the installation.

At this point, when I type
java -version 

I get 

java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.6) (6b27-1.12.6-1ubuntu0.12.04.2)
OpenJDK Server VM (build 20.0-b12, mixed mode)


but, Chrome doesn't list a java plug-in among my list of plug-ins. And Icedtea says I need to download a critical security update. I haven't been able to figure out what to do with this update once I download it (I have v. 1.2.3 at this point)- in other words, I'm not quite clear how to go about installing it. And where should I download it from?

Can anyone help me???

thanks!

p.s. and really I want OpenJDk installed and not some other flavor of Java-- this is for a certain gaming website that requires Openjdk specifically.

---

### Post by raffi_1970 on 2013-10-25
So, I went to 

this
[http://blog.fuseyism.com/index.php/2013/10/23/security-icedtea-2-4-3-released/](http://blog.fuseyism.com/index.php/2013/10/23/security-icedtea-2-4-3-released/)

and followed the directions for this security update for Icedtea.

this is what i got when I tried following the directions:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking how to create a pax tar archive... gnutar
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for style of include used by make... GNU
checking dependency style of gcc... none
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
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for make... /usr/bin/make
checking for gzip... /bin/gzip
checking for ant... no
configure: error: ant program not found in PATH


any suggestions???

thanks!

---

