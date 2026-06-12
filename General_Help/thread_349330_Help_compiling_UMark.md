---
title: "Help compiling UMark"
date: 2007-01-30
forum: General Help
---

### Post by bwhite82 on 2007-01-30
I'm having trouble compiling UMark.

Per the instructions included with the file, it says to type:

> ./autogen.sh && make

When I do so, I get:

> root@ubuntu-laptop:~/UMark# ./autogen.sh && make
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'; error while making link: File exists

automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'; error while making link: File exists

automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."

I'd appreciate any help that could be given on this, I know it can be compiled, as I've read other forum posts of people who have had the same problem, and a person helping them showed screenshots of said program. So I don't believe the problem is in the source.

---

