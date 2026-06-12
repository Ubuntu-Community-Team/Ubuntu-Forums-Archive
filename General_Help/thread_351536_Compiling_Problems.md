---
title: "Compiling Problems"
date: 2007-02-02
forum: General Help
---

### Post by D_Murdock on 2007-02-02
For some reason whenever I try to run ./configure to begin installing a piece of software I get the following error:

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking whether to enable maintainer-specific portions of Makefiles... no
configure: configuring gst-plugins for release
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Does it have to do with the BSD install line? I also tried installing Ruby with this and it spit back a compiling problem as well as some simple C programs I was working on for class. When I ran sudo aptitude install ruby it went fine. I'm not sure what is going on.

Thank you.

---

### Post by renzokuken on 2007-02-02
looks like there is a problem with the C compiler, in that it may not even be there

run 

```
sudo apt-get install build-essential
```

and try again

---

