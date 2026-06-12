---
title: "install cmdiag on Kubuntu"
date: 2015-09-08
forum: General Help
---

### Post by diari on 2015-09-08
I get this warning when I try to install cmdiag from tarball

 [FONT=monospace][COLOR=#000000] *warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] *[/COLOR][I]
         char * cm_ip = get_cmd_option(argc, argv, CMIP);
[/I]
how can I compile with C Instead of C++
[/FONT]

---

### Post by steeldriver on 2015-09-08
Hello and welcome to the forums

Warnings about deprecated code features don't usually prevent software from being built - depending how old the code base is and what language specification / compiler version it was originally developed on, a few of these are more-or-less normal in my experience

Also what makes you think it is not using C++? Although the Makefile uses $(CC) rather than the more standard $(CXX), it - unconventionally - sets this using 

```

PREFIX = /usr/sbin
EXEC = cmdiag
**CC = g++**
LIBS = `net-snmp-config --libs` `net-snmp-config --external-libs`

```

In order to get the code to build, it looks like you will need to:

[LIST=1]
[*]add the missing standard header <string.h> to cmdiag.cpp 
[*]install the libsnmp-dev package 
[*]edit the Makefile to move the -lncurses library directive to the end of the build command 
[/LIST]
[INDENT]```

$ diff Makefile{.bak,}
34c34
<     $(CC) $(CFLAGS) **-lncurses** cmdiag.o bar.o pbar.o cmodem.o func.o -o $(EXEC) $(LIBS)
---
>     $(CC) $(CFLAGS) cmdiag.o bar.o pbar.o cmodem.o func.o -o $(EXEC) **-lncurses** $(LIBS)

```
[/INDENT]

---

### Post by diari on 2015-09-08
Thank you very much, first for greetings  and for solving my problem

---

