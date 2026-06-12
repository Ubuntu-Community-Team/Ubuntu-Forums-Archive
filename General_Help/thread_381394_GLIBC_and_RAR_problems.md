---
title: "GLIBC and RAR problems"
date: 2007-03-10
forum: General Help
---

### Post by Majorix on 2007-03-10
I am a pretty new to Ubuntu so bear with me please.

Well I d/led something off the net and it was in .rar format. The PC couldn't open it by default, so I had to search for RAR Linux 3.70 beta 1 myself. I installed it but when I tried to run it, I got the following problem:

```
unrar: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by unrar)

```

So I looked around, and found out that my GLIBC version is 2.2. I knew that GLIBC comes with libc6, so I tried upgrading that. but it said I already have the newest version.

I had no choice but to grab GLIBC 2.4 off the net. I did so, and everything went fine with ./configure, but when I tried make I got this:

```
make -r PARALLELMFLAGS="" CVSOPTS="" -C ../glibc-2.4 objdir=`pwd` all
make[1]: Entering directory `/home/aytug/Desktop/glibc-2.4'
mawk -f scripts/gen-sorted.awk \
               -v subdirs='csu assert ctype locale intl catgets math setjmp signal stdlib stdio-common libio malloc string wcsmbs time dirent grp pwd posix io termios resource misc socket sysvipc gmon gnulib iconv iconvdata wctype manual shadow po argp crypt nss localedata timezone rt conform debug  dlfcn elf' \
               -v srcpfx='' \
               nptl/sysdeps/pthread/Subdirs sysdeps/unix/inet/Subdirs sysdeps/unix/Subdirs assert/Depend intl/Depend catgets/Depend stdlib/Depend stdio-common/Depend libio/Depend malloc/Depend string/Depend wcsmbs/Depend time/Depend posix/Depend iconvdata/Depend nss/Depend localedata/Depend rt/Depend debug/Depend > /home/aytug/Desktop/glibc-build/sysd-sorted-tmp
mawk: scripts/gen-sorted.awk: line 19: regular expression compile failed (bad class -- [], [^] or [)
/[^
mawk: scripts/gen-sorted.awk: line 19: syntax error at or near ]
mawk: scripts/gen-sorted.awk: line 19: runaway regular expression /, "", subd ...
make[1]: *** No rule to make target `/home/aytug/Desktop/glibc-build/Versions.all', needed by `/home/aytug/Desktop/glibc-build/abi-versions.h'.  Stop.
make[1]: Leaving directory `/home/aytug/Desktop/glibc-2.4'
make: *** [all] Error 2

```

Anybody can be of any assistance? Thanks a lot for caring.

---

### Post by zvacet on 2007-03-11
Find unrar in synaptic and install it.You can do it with Automatx or Easyubuntu too.

---

### Post by Majorix on 2007-03-11
Well even though I have multiverse and universe too enabled I can't seem to find "unrar" package. I only found "unrar-free", installed it, and when I run it I get errors like "mkdir failed <insert_directory_here>" and when I run it a few times those directories are created. But then the files cannot be created because it says "Failed" after each file's name.

I don't know what to do :confused:

---

### Post by nebc on 2007-03-12
unrar is found in the utilities repository, be sure to enable multiverse.  To do this go synaptic package manager, click on the settings menu and select repositories.  Then edit all of your checked repositories and add multiverse (This solution is a bit wasteful bit I can't remember exactly which one you need to enable).  Then click reload on the menu bar and try searching for unrar again.

---

