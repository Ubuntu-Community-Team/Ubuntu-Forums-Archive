---
title: "HTML::Parser"
date: 2007-01-24
forum: General Help
---

### Post by compuwiz on 2007-01-24
The mein thing I need to install is: HTML::Entities, which requires HTML::Parser.

I am unable to install HTML::Parser using webmin. Whn I try to do it manually, I get this error:
```

  CPAN.pm: Going to build G/GA/GAAS/HTML-Parser-3.56.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for HTML::Parser
cp lib/HTML/PullParser.pm blib/lib/HTML/PullParser.pm
cp Parser.pm blib/lib/HTML/Parser.pm
cp lib/HTML/Entities.pm blib/lib/HTML/Entities.pm
cp lib/HTML/TokeParser.pm blib/lib/HTML/TokeParser.pm
cp lib/HTML/LinkExtor.pm blib/lib/HTML/LinkExtor.pm
cp lib/HTML/Filter.pm blib/lib/HTML/Filter.pm
cp lib/HTML/HeadParser.pm blib/lib/HTML/HeadParser.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/ExtUtils/typemap -typemap typemap  Parser.xs > Parser.xsc && mv Parser.xsc Pr.c
/usr/bin/perl mkhctype >hctype.h
/usr/bin/perl mkpfunc >pfunc.h
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-sing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 - -DVERSION=\"3.56\" -DXS_VERSION=\"3.56\" -fPIC "-I/usr/lib/perl/5.8/CORE"  RKED_SECTION Parser.c
/bin/sh: cc: command not found
make: *** [Parser.o] Error 127
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

cpan>


```

after reinstalling make, I get the same error.

But this is what I get in webmin:
```
Executing /usr/bin/perl Makefile.PL  && make ..
                                                                                                    
Checking if your kit is complete...
Looks good
Writing Makefile for HTML::Parser
cp lib/HTML/PullParser.pm blib/lib/HTML/PullParser.pm
cp Parser.pm blib/lib/HTML/Parser.pm
cp lib/HTML/Entities.pm blib/lib/HTML/Entities.pm
cp lib/HTML/TokeParser.pm blib/lib/HTML/TokeParser.pm
cp lib/HTML/LinkExtor.pm blib/lib/HTML/LinkExtor.pm
cp lib/HTML/Filter.pm blib/lib/HTML/Filter.pm
cp lib/HTML/HeadParser.pm blib/lib/HTML/HeadParser.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -ty
pemap typemap  Parser.xs > Parser.xsc && mv Parser.xsc Parser.c
/usr/bin/perl mkhctype >hctype.h
/usr/bin/perl mkpfunc >pfunc.h
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/lo
cal/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"3.56\" -DXS_VERSION=\"3.56\
" -fPIC "-I/usr/lib/perl/5.8/CORE"  -DMARKED_SECTION Parser.c
/bin/sh: cc: command not found
make: *** [Parser.o] Error 127
```

---

### Post by llamakc on 2007-01-24
Why not just install via Synaptic or apt-get the following package?

> 
libhtml-parser-perl


I know this doesn't answer your webmin question, but I'm unfamiliar with executing the commandline inside of it.

---

### Post by compuwiz on 2007-01-24
Thank you. It worked. I searched for HTML::Parser but didnt find anything. But This worked, and again thanks.

---

### Post by llamakc on 2007-01-24
> **compuwiz said:**
> Thank you. It worked. I searched for HTML::Parser but didnt find anything. But This worked, and again thanks.

I'm not too knowledgeable about Synaptic, but in a terminal you can do something like:

apt-cache search html | grep parser

and scroll through the output. Perl modules are notated with *-perl btw.

---

### Post by hitter on 2007-01-28
the error was due to gcc.. install it

```
$ sudo apt-get install gcc libc6-dev
```

i think i posted these same lines in many threads.. it is a common error..

---

### Post by phossal on 2007-01-28
To address why CPAN might be failing:

It's better to install gcc and make this way:
```
sudo apt-get install build-essential
```

And then open cpan using sudo, as it will need root privileges to write in certain directories and/or use make:
```
sudo cpan
```

---

