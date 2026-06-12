---
title: "'autoconf' is missing on your system"
date: 2013-12-10
forum: General Help
---

### Post by thewillbowles on 2013-12-10
Hi all,

I am receiving the following when trying to configure and make version 8.33 of PCRE - Pear Compatible Regular Expressions:

```
will@will-ubuntu:/opt/pcre-8.33$ makeCDPATH="${ZSH_VERSION+.}:" && cd . && /bin/bash /opt/pcre-8.33/missing autoconf
/opt/pcre-8.33/missing: line 81: autoconf: command not found
WARNING: 'autoconf' is missing on your system.
         You should only need it if you modified 'configure.ac',
         or m4 files included by it.
         The 'autoconf' program is part of the GNU Autoconf package:
         <http://www.gnu.org/software/autoconf/>
         It also requires GNU m4 and Perl in order to run:
         <http://www.gnu.org/software/m4/>
         <http://www.perl.org/>
make: *** [configure] Error 127
will@will-ubuntu:/opt/pcre-8.33$
```

I have set this up many times before and never had a problem. I don't know exactly what would be causing it or what the autoconf is or does.

I am using Ubuntu 12.04.3 LTS.

Cheers

Will

---

### Post by steeldriver on 2013-12-10
What command(s) did you type exactly? was the command shown (in particular, the **/bin/bash /opt/pcre-8.33/missing autoconf** part) generated automatically or did you copy it from somewhere? It shouldn't be necessary to do anything more than

```

./configure

make

```

and like the message says, autoconf should only be required if you have modified the configure.ac template.

There's really no reason not to install autoconf as far as I know, however I don't think it will solve your issue since the 'missing' script is being called explicitly.

---

### Post by thewillbowles on 2013-12-10
Thanks for the reply.

I ran sudo ./configure --prefix=/usr/local/pcre which seemed to run fine, followed by make.

The /bin/bash/opt/pcre-8.33/missing autoconf was generated automatically after I ran make.

---

### Post by steeldriver on 2013-12-10
Hmm... well i just removed autoconf from my system and was able to configure and make it with exactly those options. I got the tarball from sourceforge.net - I didn't try to 'make install' because I don't actually want it on my system.

It sounds like either you modified one of the template files (perhaps accidentally - just enough to change its timestamp) or the timestamps got messed up when extracting the tarball - if you didn't intentionally modify anything then I suggest you 'start clean' i.e. delete the build directory and extract the tarball again.

OTOH if you deliberately modified the configuration then you will need to install autoconf

---

### Post by thewillbowles on 2013-12-10
Weirdly, this time I decided to move the extracted folder rather than copy it and it worked fine... I wonder if some of the permissions were lost when copying it or if the modified dates were all touched causing that problem?

Thanks for trying though, appreciate the help.

---

