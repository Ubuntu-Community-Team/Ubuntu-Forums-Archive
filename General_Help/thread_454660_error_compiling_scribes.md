---
title: "error compiling scribes"
date: 2007-05-25
forum: General Help
---

### Post by m0untainrebel on 2007-05-25
i've used scribes ([http://scribes.sourceforge.net/](http://scribes.sourceforge.net/)) as a programmers editor for ruby before and it's really nice. it's nice in the ubuntu repositories yet, so i need to compile it by source. i downloaded scribes-0.3.2.5, went into the directory and did ./configure, which worked fine. but then when i type make, it gives me this error:

```
Making all in po
make[1]: Entering directory `/home/micah/Desktop/scribes-0.3.2.5/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/micah/Desktop/scribes-0.3.2.5/po'
make: *** [all-recursive] Error 1
```

i have build-essentials installed. is there anything i'm doing wrong? thanks.

---

### Post by mbradlcu on 2007-05-25
it just built without issue on my 7.04_64 system.. attached is the config.log, see what differs and maybe you can find the missing dependencies..,,, or not,, looks like I the file is too large to up load so here's the relevant section
> 
configure:1883: checking for a BSD-compatible install
configure:1939: result: /usr/bin/install -c
configure:1950: checking whether build environment is sane
configure:1993: result: yes
configure:2058: checking for gawk
configure:2074: found /usr/bin/gawk
configure:2085: result: gawk
configure:2096: checking whether make sets $(MAKE)
configure:2117: result: yes
configure:2301: checking whether to enable maintainer-specific portions of Makef
iles
configure:2310: result: no
configure:2341: checking for style of include used by make
configure:2369: result: GNU
configure:2442: checking for gcc
configure:2458: found /usr/bin/gcc
configure:2469: result: gcc
configure:2707: checking for C compiler version
configure:2714: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)


---

### Post by snakedr on 2007-05-25
Check and see if the "make" package is installed.

To install:

sudo apt-get install make

---

### Post by SirOracle on 2007-05-27
Check here:
[http://ubuntuforums.org/showthread.php?t=278610&page=30](http://ubuntuforums.org/showthread.php?t=278610&page=30)

Or just type:
```
sudo aptitude install gettext
```
Then start over with ./configure again.

---

### Post by m0untainrebel on 2007-05-27
that worked! thanks so much!

---

### Post by alecwh on 2007-12-28
Just in case someone comes across this thread, I found out (after trying to compile) that scribes is in the repositories. I am using Gusty 7.10.

```
sudo apt-get install scribes
```

---

