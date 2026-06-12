---
title: "Difficulty Compiling Jabber MU-Conference Source"
date: 2013-04-01
forum: General Help
---

### Post by Kirk Schnable on 2013-04-01
I am following the tutorial for installing Jabber MU-Conference for Jabberd2.

[https://github.com/jabberd2/jabberd2/wiki/InstallGuide-MU-Conferencing](https://github.com/jabberd2/jabberd2/wiki/InstallGuide-MU-Conferencing)

I downloaded the source from [https://gna.org/projects/mu-conference/](https://gna.org/projects/mu-conference/) specifically [http://download.gna.org/mu-conference/mu-conference_0.8.tar.gz](http://download.gna.org/mu-conference/mu-conference_0.8.tar.gz).

I am running Ubuntu 12.04.2 LTS with kernel 3.2.0-23-generic.

I had some other errors at the get-go, but I have used apt to install pkg-config glib-2.0, and libglib2.0-dev.  This has resolved some errors, but I am not certain what to do about the one I'm getting now:

```
root@Endeavour:~/jabber-installations/muc/mu-conference_0.8# make
cd src/ ; make
make[1]: Entering directory `/root/jabber-installations/muc/mu-conference_0.8/src'
cd jabberd ; make
make[2]: Entering directory `/root/jabber-installations/muc/mu-conference_0.8/src/jabberd'
gcc  -O2 -Wall -I. -I../../include `pkg-config --cflags glib-2.0` -D_REENTRANT -DLIBIDN   -c -o expat.o expat.c
In file included from expat.c:42:0:
../../include/lib.h:25:19: fatal error: expat.h: No such file or directory
compilation terminated.
make[2]: *** [expat.o] Error 1
make[2]: Leaving directory `/root/jabber-installations/muc/mu-conference_0.8/src/jabberd'
make[1]: *** [libjcomp.a] Error 2
make[1]: Leaving directory `/root/jabber-installations/muc/mu-conference_0.8/src'
make: *** [all] Error 2
root@Endeavour:~/jabber-installations/muc/mu-conference_0.8#
```

I'm sure it's a pretty simple issue, I just am not that familiar with compiling programs from source, I usually use the package manager.

Thanks,
Kirk

---

### Post by Kirk Schnable on 2013-04-01
On IRC, it was recommended to me by germanmafia that I install libexpat1-dev.

This brought me to this stage, where I now have a different error.  What else am I missing?

```
root@Endeavour:~/jabber-installations/muc/mu-conference_0.8# makecd src/ ; make
make[1]: Entering directory `/root/jabber-installations/muc/mu-conference_0.8/src'
cd jabberd ; make
make[2]: Entering directory `/root/jabber-installations/muc/mu-conference_0.8/src/jabberd'
gcc  -O2 -Wall -I. -I../../include `pkg-config --cflags glib-2.0` -D_REENTRANT -DLIBIDN   -c -o expat.o expat.c
gcc  -O2 -Wall -I. -I../../include `pkg-config --cflags glib-2.0` -D_REENTRANT -DLIBIDN   -c -o jid.o jid.c
jid.c:51:26: fatal error: stringprep.h: No such file or directory
compilation terminated.
make[2]: *** [jid.o] Error 1
make[2]: Leaving directory `/root/jabber-installations/muc/mu-conference_0.8/src/jabberd'
make[1]: *** [libjcomp.a] Error 2
make[1]: Leaving directory `/root/jabber-installations/muc/mu-conference_0.8/src'
make: *** [all] Error 2
root@Endeavour:~/jabber-installations/muc/mu-conference_0.8# 
```

---

### Post by Kirk Schnable on 2013-04-01
On IRC, germanmafia recommended also installing libidn11-dev.

This resolved my issue!

---

