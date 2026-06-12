---
title: "Fatal Error installing gutenprint-5.2.13"
date: 2018-01-24
forum: General Help
---

### Post by willocid on 2018-01-24
Hello

I have a canon pixma g1100 printer. I'm trying to use the printer with ubuntu 16.04 by installing gutenprint. I have CUPS installed in my system with cups-devel (libcups2-dev and similars), but there is a fatal error when I compile gutenprint. I appreciate your help.

After ./configure

[B]================================================================
  Release: gutenprint 5.2.13 generated on 16 Jul 2017

  Features:
        Build CUPS:                                         yes, installing in /usr
        Build CUPS 1.2 enhancements:            yes
        Build CUPS PPD files:                           no
        Generate PS level 3 CUPS PPD files:     yes
        Build genppd statically:                         yes
        Build CUPS dyesub USB backend:        yes
    Build EPSON inkjet utility:                         yes
    Build enhanced Print plugin for GIMP:       yes
        GIMP plugin will be named:                  gutenprint
        Install plugin(s) in home directory:        no
    Build test programs:                                  yes
    Build testpattern generator:                       yes

  Installation summary:
    Installation prefix:                        /usr/local
    Exec prefix:                                /usr/local (${prefix})
    Data directory:                             /usr/local/share/gutenprint
    Library directory:                          /usr/local/lib/gutenprint (/usr/local/lib/gutenprint)
    XML data directory:                         /usr/local/share/gutenprint/5.2/xml
    Module directory:                           /usr/local/lib/gutenprint/5.2/modules (/usr/local/lib/gutenprint/5.2/modules)
    Install sample images:                      yes

  General configuration:
     Compiler options:                           -Disfinite=finite  -O6   -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes  -Wmissing-declarations -Wnested-externs -Wwrite-strings  -Werror-implicit-function-declaration -Winline -Wformat=2  -finline-limit=131072
    Build static libraries:                     yes
    Build shared libraries:                     yes
    Maintainer mode:                            no
    Use i18n:                                         yes
    Generate profiling information:       no
    Generate debugging symbols:        no
    Use modules:                                static
    Use readline libraries:                     yes
     uname -a output:                            Linux w***  4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017  x86_64 x86_64 x86_64 GNU/Linux
================================================================

[/B]After make[B][B]

genppd.c:81:25: fatal error: cups/raster.h: No such file or directory
compilation terminated.
Makefile:1423: recipe for target 'gutenprint_5.2-genppd.o' failed
make[3]: *** [gutenprint_5.2-genppd.o] Error 1
make[3]: Leaving directory '/home/Downloads/gutenprint-5.2.13/src/cups'
Makefile:468: recipe for target 'all-recursive' failed
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/[/B][/B]**[B][B][B]Downloads**[/B]/gutenprint-5.2.13/src'
Makefile:569: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/[/B][/B]**[B][B][B]Downloads**[/B]/gutenprint-5.2.13'
Makefile:499: recipe for target 'all' failed
make: *** [all] Error 2[/B][/B]

---

