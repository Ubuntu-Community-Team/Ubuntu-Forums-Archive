---
title: "Ubuntu Studio and Ptabtools"
date: 2007-12-30
forum: General Help
---

### Post by salempc on 2007-12-30
First post and already asking for help ;)

I already found a thread where someone was trying to install this, but it didn't have a happy ending.

Anyway, I'm following the basic steps on installing a .tar.gz file, and it all goes well, except for the last step....

So I get this when I introduce the 'make' command:

```
paulo@paulo:~/ptabtools-0.5.0$ make
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -fPIC -c ptb.c -o ptb.po
ptb.c: In function ‘ptb_data_instrument’:
ptb.c:540: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:541: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:542: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:543: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:544: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:545: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:546: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:547: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CSection’:
ptb.c:705: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:706: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:707: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:708: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:711: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CPosition’:
ptb.c:936: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -fPIC -c gp.c -o gp.po
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -fPIC -c ptb-tuning.c -o ptb-tuning.po
gcc -shared -Wl,-soname,libptb.so.0 -Wl,-soname,libptb.so.0 -Wl,libptb.so.0.5.0 -g -O2 -g -Wall  -DHAVE_CONFIG_H= -o libptb.so.0.5.0 ptb.po gp.po ptb-tuning.po
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -c ptb.c -o ptb.o
ptb.c: In function ‘ptb_data_instrument’:
ptb.c:540: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:541: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:542: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:543: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:544: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:545: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:546: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:547: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CSection’:
ptb.c:705: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:706: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:707: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:708: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:711: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CPosition’:
ptb.c:936: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -c gp.c -o gp.o
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -c ptb-tuning.c -o ptb-tuning.o
ar rs libptb.a ptb.o gp.o ptb-tuning.o
ar: creating libptb.a

```

I ignored the thousands of warnings, and typed in 'sudo make install' to finish it off:

```
paulo@paulo:~/ptabtools-0.5.0$ sudo make install
[sudo] password for paulo:
/usr/bin/install -c -d /usr/local/bin
test -z "" || /usr/bin/install -c  /usr/local/bin
/usr/bin/install -c -d /usr/local/share/man/man1
/usr/bin/install -c -m 644  /usr/local/share/man/man1
/usr/bin/install: missing destination file operand after `/usr/local/share/man/man1'
Try `/usr/bin/install --help' for more information.
make: *** [install] Error 1

```

Now this thing is not in the repositories, or I don't know how to put it in synaptic manager, anyway, help is always appreciated ;)
Also if you can tell me of another program that can open .ptb files then I'll forget about this one ;)

Thanks in advance

---

