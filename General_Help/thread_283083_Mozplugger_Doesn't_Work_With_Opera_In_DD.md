---
title: "Mozplugger Doesn't Work With Opera In DD"
date: 2006-10-23
forum: General Help
---

### Post by Mark76 on 2006-10-23
And I'm sick and tired of trying to get it to work ](*,)

---

### Post by skymt on 2006-10-23
You're correct, Mozplugger doesn't work with Opera. It just doesn't.

...The package version, anyway. You may have better luck downloading the [source](http://mozplugger.mozdev.org/files/mozplugger-1.7.3.tar.gz) and compiling it yourself, then using "make localinstall_opera" to install. I can't guarantee it, though. You should also learn the syntax used in mozpluggerrc, and see if you can tweak it.

---

### Post by Mark76 on 2006-10-23
Oh thank God, I thought I was going mad.

---

### Post by Mark76 on 2006-10-23
Hmm.

Why does make localinstall_opera give me this

make: *** No rule to make target `localinstall_opera'. Stop.?

---

### Post by skymt on 2006-10-23
You need to run a plain "make" first:```
make linux
make localinstall_opera
```

That should work, if I'm reading the Makefile right.

---

### Post by Mark76 on 2006-10-23
make linux
make: *** No rule to make target `linux'. Stop.
make
make: *** No targets specified and no makefile found. Stop.

---

### Post by skymt on 2006-10-23
> **Mark76 said:**
> make linux
make: *** No rule to make target `linux'. Stop.
make
make: *** No targets specified and no makefile found. Stop.

You untar'd the mozplugger archive and cd'd to the directory, right?```
cd Desktop
tar xf mozplugger-1.7.3.tar.gz
cd mozplugger-1.7.3
make linux
```That worked for me when I tried it just now.

---

### Post by Mark76 on 2006-10-23
Yikes.  So many syntax errors :eek:

mark-williams@cpc1-nfds11-0-0-cust975williams:~$ tar xvzf /home/mark-williams/Desktop/mozplugger-1.7.3.tar.gz
mozplugger-1.7.3/
mozplugger-1.7.3/ChangeLog
mozplugger-1.7.3/COPYING
mozplugger-1.7.3/npapi/
mozplugger-1.7.3/npapi/common/
mozplugger-1.7.3/npapi/common/npunix.c
mozplugger-1.7.3/npapi/include/
mozplugger-1.7.3/npapi/include/jri_md.h
mozplugger-1.7.3/npapi/include/jri.h
mozplugger-1.7.3/npapi/include/jritypes.h
mozplugger-1.7.3/npapi/include/npapi.h
mozplugger-1.7.3/npapi/include/npupp.h
mozplugger-1.7.3/Makefile
mozplugger-1.7.3/README
mozplugger-1.7.3/mozplugger-common.c
mozplugger-1.7.3/mozplugger-controller.c
mozplugger-1.7.3/mozplugger-helper.c
mozplugger-1.7.3/mozplugger.7.bz2
mozplugger-1.7.3/mozplugger.c
mozplugger-1.7.3/mozplugger.h
mozplugger-1.7.3/mozplugger.spec
mozplugger-1.7.3/mozpluggerrc
mark-williams@cpc1-nfds11-0-0-cust975williams:~$ cd/desktop
bash: cd/desktop: No such file or directory
mark-williams@cpc1-nfds11-0-0-cust975williams:~$ cd/Desktop
bash: cd/Desktop: No such file or directory
mark-williams@cpc1-nfds11-0-0-cust975williams:~$ cd Desktop
mark-williams@cpc1-nfds11-0-0-cust975williams:~/Desktop$ tar xf /home/mark-williams/Desktop/mozplugger-1.7.3.tar.gz
mark-williams@cpc1-nfds11-0-0-cust975williams:~/Desktop$ cd mozplugger-1.7.3
mark-williams@cpc1-nfds11-0-0-cust975williams:~/Desktop/mozplugger-1.7.3$ make linux
make all CC=gcc XCFLAGS=-fPIC LD=gcc XLDFLAGS=-shared
make[1]: Entering directory `/home/mark-williams/Desktop/mozplugger-1.7.3'
gcc -c -O2 -Inpapi/include -I/usr/X11R6/include -DXP_UNIX  -DVERSION=\"1.7.3\" -fPIC -o mozplugger.o mozplugger.c
In file included from mozplugger.h:8,
                 from mozplugger.c:20:
npapi/include/npapi.h:129:22: error: X11/Xlib.h: No such file or directory
In file included from mozplugger.h:8,
                 from mozplugger.c:20:
npapi/include/npapi.h:148: error: syntax error before &#8216;Display&#8217;
npapi/include/npapi.h:148: warning: no semicolon at end of struct or union
npapi/include/npapi.h:149: warning: data definition has no type or storage classnpapi/include/npapi.h:150: error: syntax error before &#8216;colormap&#8217;
npapi/include/npapi.h:150: warning: data definition has no type or storage classnpapi/include/npapi.h:152: error: syntax error before &#8216;}&#8217; token
npapi/include/npapi.h:152: warning: data definition has no type or storage classIn file included from mozplugger.c:20:
mozplugger.h:13:19: error: X11/X.h: No such file or directory
mozplugger.h:14:21: error: X11/Xos.h: No such file or directory
mozplugger.h:15:27: error: X11/Intrinsic.h: No such file or directory
mozplugger.h:16:23: error: X11/Xatom.h: No such file or directory
mozplugger.c:39: error: syntax error before &#8216;Display&#8217;
mozplugger.c:39: warning: no semicolon at end of struct or union
mozplugger.c:55: error: syntax error before &#8216;}&#8217; token
mozplugger.c:55: warning: data definition has no type or storage class
mozplugger.c: In function &#8216;my_fork&#8217;:
mozplugger.c:117: error: syntax error before &#8216;)&#8217; token
mozplugger.c:123: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;run&#8217;:
mozplugger.c:168: error: syntax error before &#8216;)&#8217; token
mozplugger.c:168: error: syntax error before &#8216;)&#8217; token
mozplugger.c:169: error: syntax error before &#8216;)&#8217; token
mozplugger.c:172: error: syntax error before &#8216;)&#8217; token
mozplugger.c:173: error: syntax error before &#8216;)&#8217; token
mozplugger.c:174: error: syntax error before &#8216;)&#8217; token
mozplugger.c:175: error: syntax error before &#8216;)&#8217; token
mozplugger.c:176: error: syntax error before &#8216;)&#8217; token
mozplugger.c:177: error: syntax error before &#8216;)&#8217; token
mozplugger.c:178: error: syntax error before &#8216;)&#8217; token
mozplugger.c:179: error: syntax error before &#8216;)&#8217; token
mozplugger.c:185: error: syntax error before &#8216;)&#8217; token
mozplugger.c:186: error: syntax error before &#8216;)&#8217; token
mozplugger.c:187: error: syntax error before &#8216;)&#8217; token
mozplugger.c:191: error: syntax error before &#8216;)&#8217; token
mozplugger.c:194: error: syntax error before &#8216;)&#8217; token
mozplugger.c:197: error: syntax error before &#8216;)&#8217; token
mozplugger.c:200: error: syntax error before &#8216;)&#8217; token
mozplugger.c:203: error: syntax error before &#8216;)&#8217; token
mozplugger.c:206: error: syntax error before &#8216;)&#8217; token
mozplugger.c:210: error: syntax error before &#8216;)&#8217; token
mozplugger.c:212: error: syntax error before &#8216;)&#8217; token
mozplugger.c:213: error: syntax error before &#8216;)&#8217; token
mozplugger.c:215: error: syntax error before &#8216;)&#8217; token
mozplugger.c:216: error: syntax error before &#8216;)&#8217; token
mozplugger.c:221: error: syntax error before &#8216;)&#8217; token
mozplugger.c:222: error: syntax error before &#8216;)&#8217; token
mozplugger.c:223: error: syntax error before &#8216;)&#8217; token
mozplugger.c:223: error: syntax error before &#8216;)&#8217; token
mozplugger.c:225: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;read_config_cb&#8217;:
mozplugger.c:601: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
mozplugger.c:601: error: (Each undeclared identifier is reported only once
mozplugger.c:601: error: for each function it appears in.)
mozplugger.c: In function &#8216;match_command&#8217;:
mozplugger.c:727: error: syntax error before &#8216;)&#8217; token
mozplugger.c:741: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;match_mime_type&#8217;:
mozplugger.c:763: error: syntax error before &#8216;)&#8217; token
mozplugger.c:764: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;match_handler&#8217;:
mozplugger.c:794: error: syntax error before &#8216;)&#8217; token
mozplugger.c:795: error: syntax error before &#8216;)&#8217; token
mozplugger.c:796: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;NPP_New&#8217;:
mozplugger.c:983: error: syntax error before &#8216;)&#8217; token
mozplugger.c:984: error: syntax error before &#8216;)&#8217; token
mozplugger.c:985: error: syntax error before &#8216;)&#8217; token
mozplugger.c:987: error: syntax error before &#8216;)&#8217; token
mozplugger.c:988: error: syntax error before &#8216;)&#8217; token
mozplugger.c:989: error: syntax error before &#8216;)&#8217; token
mozplugger.c:990: error: syntax error before &#8216;)&#8217; token
mozplugger.c:991: error: syntax error before &#8216;)&#8217; token
mozplugger.c:992: error: syntax error before &#8216;)&#8217; token
mozplugger.c:993: error: syntax error before &#8216;)&#8217; token
mozplugger.c:995: error: syntax error before &#8216;)&#8217; token
mozplugger.c:998: error: syntax error before &#8216;)&#8217; token
mozplugger.c:999: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1006: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1010: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1019: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1021: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1022: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1032: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1034: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1045: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;NPP_Destroy&#8217;:
mozplugger.c:1066: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1069: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1070: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1072: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1073: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1075: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1077: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1078: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1081: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1083: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1084: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1085: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1087: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1088: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;new_child&#8217;:
mozplugger.c:1108: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1117: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1120: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1125: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1135: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;NPP_NewStream&#8217;:
mozplugger.c:1155: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1162: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1168: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1168: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1171: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1184: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;resize_window&#8217;:
mozplugger.c:1213: error: &#8216;XSetWindowAttributes&#8217; undeclared (first use in this function)
mozplugger.c:1213: error: syntax error before &#8216;attrib&#8217;
mozplugger.c:1214: error: &#8216;attrib&#8217; undeclared (first use in this function)
mozplugger.c:1214: error: &#8216;True&#8217; undeclared (first use in this function)
mozplugger.c:1215: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1215: error: &#8216;Window&#8217; undeclared (first use in this function)
mozplugger.c:1215: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1216: error: &#8216;CWOverrideRedirect&#8217; undeclared (first use in this function)
mozplugger.c:1218: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1219: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1219: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1220: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1220: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1221: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1221: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;NPP_SetWindow&#8217;:
mozplugger.c:1243: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1243: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1244: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1244: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1245: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1247: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1249: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1250: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1251: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1255: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1257: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1258: error: syntax error before &#8216;)&#8217; token
make[1]: *** [mozplugger.o] Error 1
make[1]: Leaving directory `/home/mark-williams/Desktop/mozplugger-1.7.3'
make: *** [linux] Error 2
mark-williams@cpc1-nfds11-0-0-cust975williams:~/Desktop/mozplugger-1.7.3$ make localinstall_opera
make localinstall BROWSERDIR=.opera
make[1]: Entering directory `/home/mark-williams/Desktop/mozplugger-1.7.3'
gcc -c -O2 -Inpapi/include -I/usr/X11R6/include -DXP_UNIX  -DVERSION=\"1.7.3\" -shared -o mozplugger.o mozplugger.c
In file included from mozplugger.h:8,
                 from mozplugger.c:20:
npapi/include/npapi.h:129:22: error: X11/Xlib.h: No such file or directory
In file included from mozplugger.h:8,
                 from mozplugger.c:20:
npapi/include/npapi.h:148: error: syntax error before &#8216;Display&#8217;
npapi/include/npapi.h:148: warning: no semicolon at end of struct or union
npapi/include/npapi.h:149: warning: data definition has no type or storage classnpapi/include/npapi.h:150: error: syntax error before &#8216;colormap&#8217;
npapi/include/npapi.h:150: warning: data definition has no type or storage classnpapi/include/npapi.h:152: error: syntax error before &#8216;}&#8217; token
npapi/include/npapi.h:152: warning: data definition has no type or storage classIn file included from mozplugger.c:20:
mozplugger.h:13:19: error: X11/X.h: No such file or directory
mozplugger.h:14:21: error: X11/Xos.h: No such file or directory
mozplugger.h:15:27: error: X11/Intrinsic.h: No such file or directory
mozplugger.h:16:23: error: X11/Xatom.h: No such file or directory
mozplugger.c:39: error: syntax error before &#8216;Display&#8217;
mozplugger.c:39: warning: no semicolon at end of struct or union
mozplugger.c:55: error: syntax error before &#8216;}&#8217; token
mozplugger.c:55: warning: data definition has no type or storage class
mozplugger.c: In function &#8216;my_fork&#8217;:
mozplugger.c:117: error: syntax error before &#8216;)&#8217; token
mozplugger.c:123: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;run&#8217;:
mozplugger.c:168: error: syntax error before &#8216;)&#8217; token
mozplugger.c:168: error: syntax error before &#8216;)&#8217; token
mozplugger.c:169: error: syntax error before &#8216;)&#8217; token
mozplugger.c:172: error: syntax error before &#8216;)&#8217; token
mozplugger.c:173: error: syntax error before &#8216;)&#8217; token
mozplugger.c:174: error: syntax error before &#8216;)&#8217; token
mozplugger.c:175: error: syntax error before &#8216;)&#8217; token
mozplugger.c:176: error: syntax error before &#8216;)&#8217; token
mozplugger.c:177: error: syntax error before &#8216;)&#8217; token
mozplugger.c:178: error: syntax error before &#8216;)&#8217; token
mozplugger.c:179: error: syntax error before &#8216;)&#8217; token
mozplugger.c:185: error: syntax error before &#8216;)&#8217; token
mozplugger.c:186: error: syntax error before &#8216;)&#8217; token
mozplugger.c:187: error: syntax error before &#8216;)&#8217; token
mozplugger.c:191: error: syntax error before &#8216;)&#8217; token
mozplugger.c:194: error: syntax error before &#8216;)&#8217; token
mozplugger.c:197: error: syntax error before &#8216;)&#8217; token
mozplugger.c:200: error: syntax error before &#8216;)&#8217; token
mozplugger.c:203: error: syntax error before &#8216;)&#8217; token
mozplugger.c:206: error: syntax error before &#8216;)&#8217; token
mozplugger.c:210: error: syntax error before &#8216;)&#8217; token
mozplugger.c:212: error: syntax error before &#8216;)&#8217; token
mozplugger.c:213: error: syntax error before &#8216;)&#8217; token
mozplugger.c:215: error: syntax error before &#8216;)&#8217; token
mozplugger.c:216: error: syntax error before &#8216;)&#8217; token
mozplugger.c:221: error: syntax error before &#8216;)&#8217; token
mozplugger.c:222: error: syntax error before &#8216;)&#8217; token
mozplugger.c:223: error: syntax error before &#8216;)&#8217; token
mozplugger.c:223: error: syntax error before &#8216;)&#8217; token
mozplugger.c:225: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;read_config_cb&#8217;:
mozplugger.c:601: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
mozplugger.c:601: error: (Each undeclared identifier is reported only once
mozplugger.c:601: error: for each function it appears in.)
mozplugger.c: In function &#8216;match_command&#8217;:
mozplugger.c:727: error: syntax error before &#8216;)&#8217; token
mozplugger.c:741: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;match_mime_type&#8217;:
mozplugger.c:763: error: syntax error before &#8216;)&#8217; token
mozplugger.c:764: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;match_handler&#8217;:
mozplugger.c:794: error: syntax error before &#8216;)&#8217; token
mozplugger.c:795: error: syntax error before &#8216;)&#8217; token
mozplugger.c:796: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;NPP_New&#8217;:
mozplugger.c:983: error: syntax error before &#8216;)&#8217; token
mozplugger.c:984: error: syntax error before &#8216;)&#8217; token
mozplugger.c:985: error: syntax error before &#8216;)&#8217; token
mozplugger.c:987: error: syntax error before &#8216;)&#8217; token
mozplugger.c:988: error: syntax error before &#8216;)&#8217; token
mozplugger.c:989: error: syntax error before &#8216;)&#8217; token
mozplugger.c:990: error: syntax error before &#8216;)&#8217; token
mozplugger.c:991: error: syntax error before &#8216;)&#8217; token
mozplugger.c:992: error: syntax error before &#8216;)&#8217; token
mozplugger.c:993: error: syntax error before &#8216;)&#8217; token
mozplugger.c:995: error: syntax error before &#8216;)&#8217; token
mozplugger.c:998: error: syntax error before &#8216;)&#8217; token
mozplugger.c:999: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1006: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1010: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1019: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1021: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1022: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1032: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1034: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1045: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;NPP_Destroy&#8217;:
mozplugger.c:1066: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1069: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1070: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1072: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1073: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1075: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1077: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1078: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1081: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1083: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1084: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1085: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1087: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1088: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;new_child&#8217;:
mozplugger.c:1108: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1117: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1120: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1125: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1135: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;NPP_NewStream&#8217;:
mozplugger.c:1155: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1162: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1168: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1168: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1171: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1184: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;resize_window&#8217;:
mozplugger.c:1213: error: &#8216;XSetWindowAttributes&#8217; undeclared (first use in this function)
mozplugger.c:1213: error: syntax error before &#8216;attrib&#8217;
mozplugger.c:1214: error: &#8216;attrib&#8217; undeclared (first use in this function)
mozplugger.c:1214: error: &#8216;True&#8217; undeclared (first use in this function)
mozplugger.c:1215: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1215: error: &#8216;Window&#8217; undeclared (first use in this function)
mozplugger.c:1215: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1216: error: &#8216;CWOverrideRedirect&#8217; undeclared (first use in this function)
mozplugger.c:1218: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1219: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1219: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1220: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1220: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1221: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1221: error: syntax error before &#8216;)&#8217; token
mozplugger.c: In function &#8216;NPP_SetWindow&#8217;:
mozplugger.c:1243: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1243: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1244: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1244: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1245: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1247: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1249: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1250: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1251: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1255: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1257: error: syntax error before &#8216;)&#8217; token
mozplugger.c:1258: error: syntax error before &#8216;)&#8217; token
make[1]: *** [mozplugger.o] Error 1
make[1]: Leaving directory `/home/mark-williams/Desktop/mozplugger-1.7.3'
make: *** [localinstall_opera] Error 2
mark-williams@cpc1-nfds11-0-0-cust975williams:~/Desktop/mozplugger-1.7.3$

---

### Post by skymt on 2006-10-24
Do you have libx11-dev installed? If not, do so.

---

### Post by Mark76 on 2006-10-24
I didn't, but I installed it and then tried again from cd mozplugger 1.7.3.

Does this look right?

mark-williams@cpc1-nfds11-0-0-cust975williams:~$ cd /home/mark-williams/mozplugger-1.7.3
mark-williams@cpc1-nfds11-0-0-cust975williams:~/mozplugger-1.7.3$ make linux
make all CC=gcc XCFLAGS=-fPIC LD=gcc XLDFLAGS=-shared
make[1]: Entering directory `/home/mark-williams/mozplugger-1.7.3'
gcc -c -O2 -Inpapi/include -I/usr/X11R6/include -DXP_UNIX  -DVERSION=\"1.7.3\" -fPIC -o mozplugger.o mozplugger.c
In file included from mozplugger.c:20:
mozplugger.h:15:27: error: X11/Intrinsic.h: No such file or directory
make[1]: *** [mozplugger.o] Error 1
make[1]: Leaving directory `/home/mark-williams/mozplugger-1.7.3'
make: *** [linux] Error 2
mark-williams@cpc1-nfds11-0-0-cust975williams:~/mozplugger-1.7.3$

---

### Post by skymt on 2006-10-24
It looks like you also need to install libxt-dev.

For this sort of thing, the [Ubuntu Package Database](http://packages.ubuntu.com/) is useful. For example, I saw in your error message that it was missing a file called "Intrinsic.h". I searched the Database (using the second search box, the one that says "Search the contents of packages"), and came up with two results. Only libxt-dev is a development library (in the "libdevel" section), so that's what you need.

---

### Post by Mark76 on 2006-10-24
Okay, installed that.  Tried again and got

mark-williams@cpc1-nfds11-0-0-cust975williams:~$ cd mozplugger-1.7.3
mark-williams@cpc1-nfds11-0-0-cust975williams:~/mozplugger-1.7.3$ make linux
make all CC=gcc XCFLAGS=-fPIC LD=gcc XLDFLAGS=-shared
make[1]: Entering directory `/home/mark-williams/mozplugger-1.7.3'
gcc -c -O2 -Inpapi/include -I/usr/X11R6/include -DXP_UNIX  -DVERSION=\"1.7.3\" -fPIC -o mozplugger.o mozplugger.c
gcc -c -O2 -Inpapi/include -I/usr/X11R6/include -DXP_UNIX  -DVERSION=\"1.7.3\" -fPIC -o stub.o npapi/common/npunix.c
gcc -c -O2 -Inpapi/include -I/usr/X11R6/include -DXP_UNIX  -DVERSION=\"1.7.3\" -fPIC -o mozplugger-common.o mozplugger-common.c
gcc -shared   -o mozplugger.so mozplugger.o mozplugger-common.o stub.o
gcc -O2 -Inpapi/include -I/usr/X11R6/include -DXP_UNIX  -DVERSION=\"1.7.3\" -c -o mozplugger-helper.o mozplugger-helper.c
mozplugger-helper.c: In function &#8216;winrecur&#8217;:
mozplugger-helper.c:252: warning: pointer targets in passing argument 6 of &#8216;XQueryTree&#8217; differ in signedness
gcc   -o mozplugger-helper mozplugger-helper.o mozplugger-common.o -lX11 -L/usr/X11R6/lib
gcc -O2 -Inpapi/include -I/usr/X11R6/include -DXP_UNIX  -DVERSION=\"1.7.3\" -c -o mozplugger-controller.o mozplugger-controller.c
gcc -o mozplugger-controller mozplugger-controller.o mozplugger-common.o   -lX11 -L/usr/X11R6/lib
make[1]: Leaving directory `/home/mark-williams/mozplugger-1.7.3'
mark-williams@cpc1-nfds11-0-0-cust975williams:~/mozplugger-1.7.3$ make localinstall_opera
make localinstall BROWSERDIR=.opera
make[1]: Entering directory `/home/mark-williams/mozplugger-1.7.3'
cp mozplugger.so $HOME/.opera/plugins/
cp mozplugger-helper $HOME/.opera/
cp mozplugger-controller $HOME/.opera/
if [ -f $HOME/.opera/mozpluggerrc ]; then mv $HOME/.opera/mozpluggerrc $HOME/.opera/mozpluggerrc.old; fi
cp mozpluggerrc $HOME/.opera/
make[1]: Leaving directory `/home/mark-williams/mozplugger-1.7.3'
mark-williams@cpc1-nfds11-0-0-cust975williams:~/mozplugger-1.7.3$

---

### Post by Mark76 on 2006-10-24
Do these plugin paths look screwed up?

---

### Post by skymt on 2006-10-24
Now that you have Mozplugger 1.7.3 installed locally, you should remove the packaged version.

Yes, the plugin paths are fine.

---

### Post by Mark76 on 2006-10-24
I did all you said and tried to stream a song from a site I visit, but all I got was this

---

### Post by skymt on 2006-10-24
Mozplugger probably isn't set up to stream RealAudio. You'll need to change your mozpluggerrc. If it is set up properly, and it still doesn't stream, then it can't be done with Mozplugger/Opera. You'll need the official Real player/plugin.

Plugin writers really need to work on Opera compatibility. The only plugin I've gotten to *reliably* work in Opera is Flash. Everything else is iffy at best.

---

### Post by Mark76 on 2006-10-24
Where exactly do I go to change my mozpluggerrc?

I'm guessing it's in the folder, but once I get there it'll probably tell me I don't have permission to edit anything :(

---

### Post by skymt on 2006-10-24
> **Mark76 said:**
> Where exactly do I go to change my mozpluggerrc?

I'm guessing it's in the folder, but once I get there it'll probably tell me I don't have permission to edit anything :(

It should be at "~/.opera/mozpluggerrc". You also should have permission to edit it, since it's a user-level install, not system-level like the packaged version is.

---

### Post by Mark76 on 2006-10-24
Why are these things always against me?

mark-williams@cpc1-nfds11-0-0-cust975williams:~$ ~/.opera/mozpluggerrc
bash: /home/mark-williams/.opera/mozpluggerrc: Permission denied
mark-williams@cpc1-nfds11-0-0-cust975williams:~$ sudo ~/.opera/mozpluggerrc
Password:
sudo: /home/mark-williams/.opera/mozpluggerrc: command not found
mark-williams@cpc1-nfds11-0-0-cust975williams:~$

---

### Post by skymt on 2006-10-24
> **Mark76 said:**
> Why are these things always against me?

mark-williams@cpc1-nfds11-0-0-cust975williams:~$ ~/.opera/mozpluggerrc
bash: /home/mark-williams/.opera/mozpluggerrc: Permission denied
mark-williams@cpc1-nfds11-0-0-cust975williams:~$ sudo ~/.opera/mozpluggerrc
Password:
sudo: /home/mark-williams/.opera/mozpluggerrc: command not found
mark-williams@cpc1-nfds11-0-0-cust975williams:~$

You need to edit it, not run it:```
gedit ~/.opera/mozpluggerrc
```

---

### Post by Mark76 on 2006-10-24
Okay. Once I have gedit open what am I looking for and what do I do when I've found it?

---

### Post by skymt on 2006-10-24
Do you have mplayer installed? If so, copy this to the end of your mozpluggerrc:```
audio/x-pn-realaudio:ra,rm,ram:Realaudio-plugin resource locator
audio/x-realaudio:ra,rm,ram:RealAudio file
audio/vnd.rn-realaudio:ra,ram:RealAudio file
	MP_AUDIO_STREAM()
```The mozpluggerrc Ubuntu ships in the packaged version includes a section that uses the official Realplayer for Real files. I just took that and removed the video stuff, and told it to use mplayer instead of Realplayer.

---

### Post by Mark76 on 2006-10-24
I have both Mplayer and Mozilla installed but that didn't work either.

Maybe if I reboot.

---

### Post by Mark76 on 2006-10-24
Nope that didn't help.

Did you change stuff in 

> audio/x-pn-realaudio:ra,rm,ram:Realaudio-plugin resource locator
audio/x-realaudio:ra,rm,ram:RealAudio file
audio/vnd.rn-realaudio:ra,ram:RealAudio file
	MP_AUDIO_STREAM()

And forget to tell me what?

---

### Post by skymt on 2006-10-24
If you just want Real audio, it would probably be much less painful to just [install Realplayer](https://help.ubuntu.com/community/RealplayerInstallationMethods). As you're seeing, Mozplugger is tough to get working, especially with Opera.

---

### Post by Mark76 on 2006-10-24
I want the audio at this site [www.indiepages.com](www.indiepages.com) to work

I can't download the review clips

And I already have Realplay

---

### Post by skymt on 2006-10-24
Does the Real plugin show up in about:plugins?

---

### Post by Mark76 on 2006-10-25
Yep. Twice

---

### Post by skymt on 2006-10-25
There's your problem: you have the mplayer plugin installed. It's incompatible with Opera, and it's grabbing the Real file types. Remove it, and see if things improve.

---

### Post by Mark76 on 2006-10-25
Okay I removed it and...


Still the same.

I wish Opera would get its owned damned plugins instead of piggybacking on Mozilla ](*,)

---

### Post by skymt on 2006-10-25
What other plugins do you have? I know the Real plugin can work in Opera.

---

### Post by Mark76 on 2006-10-25
The ones you see in this screen shot

---

### Post by skymt on 2006-10-25
Try changing your plugin path to only include the Real plugin.

If you want to do it manually, you can download the Real files and play them in the standalone Realplayer.

---

### Post by Mark76 on 2006-10-25
Did that and it still doesn't work.

I'm beginning to think the page in question is at fault

[http://www.indiepages.com/reviews/index.html](http://www.indiepages.com/reviews/index.html)

---

### Post by skymt on 2006-10-25
> **Mark76 said:**
> Did that and it still doesn't work.

I'm beginning to think the page in question is at fault

[http://www.indiepages.com/reviews/index.html](http://www.indiepages.com/reviews/index.html)

Try again. I was able to manually download and play a song from that site (in mplayer, I don't have Real right now).

---

### Post by Mark76 on 2006-10-26
Nothing works :(

---

### Post by Mark76 on 2006-10-26
Take another look at my plugins path (this is from Tools/Advanced/Content)

Are you _SURE_ it's not shagged? :-k

---

### Post by picpak on 2006-10-26
I got Mozplugger working with Opera, but I don't know how. Maybe try installing m4? That fixed my problems.

---

### Post by Mark76 on 2006-10-26
According to my repository I already have M4 installed.

---

