---
title: "no c compiler error"
date: 2007-07-04
forum: General Help
---

### Post by Goda on 2007-07-04
when Im trying to compile and install a program from source I get this
```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

---

### Post by christhemonkey on 2007-07-04
Do you have build-essential installed?
```
sudo apt-get install build-essential 
```

It contains all the basic tools for compiling.


EDIT: G++ is (mainly) a C++ compiler, it is looking for a C compiler, gcc would be the usual candidate for this.

---

### Post by divague on 2007-07-04
do you have g++ installed? that's the c compiler

---

### Post by altonbr on 2007-07-04
> **christhemonkey said:**
> Do you have build-essential installed?
```
sudo apt-get install build-essential 
```

It contains all the basic tools for compiling.

I second this. You need this to compile source code.

---

### Post by Goda on 2007-07-05
I have build-essential
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
```

---

### Post by bodhi.zazen on 2007-07-05
OK, check either the README or config.log to see what version of gcc is required.

What are you trying to compile ?

---

### Post by Goda on 2007-07-06
I am trying to compile the FreeCiv beta, but I have had this problem before on a program a while ago. The install instructions say only this about gcc "Note that there have been reports that gcc with -O3 miscompiled
freeciv. No problems have been reported with -O2." Is it possible that something is wrong with gcc?

---

### Post by bodhi.zazen on 2007-07-06
> **Goda said:**
> I am trying to compile the FreeCiv beta, but I have had this problem before on a program a while ago. The install instructions say only this about gcc "Note that there have been reports that gcc with -O3 miscompiled
freeciv. No problems have been reported with -O2." Is it possible that something is wrong with gcc?

Well, I would think gcc is OK, sounds like FreeCiv has issues with -O3

---

