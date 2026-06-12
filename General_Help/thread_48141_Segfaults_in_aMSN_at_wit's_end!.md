---
title: "Segfaults in aMSN: at wit's end!"
date: 2005-07-11
forum: General Help
---

### Post by FishFace on 2005-07-11
Hi,

I've had this problem for something like a month. It appeared to start after I upgraded some packages, including backports. I've sinced uninstalled **every** backport and a couple of other packages such as tcltls, libssl-dev and so on, that may pertain to amsn. Still the segfaults go on.

They occur partly randomly, and partly causally, for example, whenever I received a new custom emoticon, I get a crash, but sometimes I get one as soon as I sign on, sometimes after several minutes. A gdb backtrace puts the segfault in libXft, but I'm pretty certain nothing related to X had been updated around then.

As well as uninstalling/rolling back packages, I have tried: Reinstalling amsn, resetting amsn config, using amsn-0.94 (I usually use cvs) recompiling amsn and repeatedly rebooting the computer. So far, nothing has worked and I'm forced to use the hunk-of-junk named gaim (junk at least with respect to its MSN capabilities) I doubt anyone else has experienced this due to repeated googlings, but anyone in the know I would GREATLY appreciate some help from. At the moment I'm looking for the best way to downgrade all packages to a base Hoary install and start from scratch, but without losing all my config on the way, or having to format the partition.

Ideas for solutions, or ways to reinstall - I just want to get aMSN back.

EDIT: Example backtrace:

```
Program received signal SIGSEGV, Segmentation fault.
0xb7d5fcbc in XftCharIndex () from /usr/lib/libXft.so.2
(gdb) bt
#0  0xb7d5fcbc in XftCharIndex () from /usr/lib/libXft.so.2
#1  0xb7d5c8c4 in XftTextExtents32 () from /usr/lib/libXft.so.2
#2  0xb7fb9f48 in Tk_MeasureChars () from /usr/local/lib/libtk8.5.so
#3  0xb7fab66f in MeasureChars () from /usr/local/lib/libtk8.5.so
#4  0xb7faab60 in TkTextCharLayoutProc () from /usr/local/lib/libtk8.5.so
#5  0xb7fa4969 in LayoutDLine () from /usr/local/lib/libtk8.5.so
#6  0xb7fa6dbf in CalculateDisplayLineHeight () from /usr/local/lib/libtk8.5.so
#7  0xb7fa6f1d in TkTextUpdateOneLine () from /usr/local/lib/libtk8.5.so
#8  0xb7fa65c4 in TkTextUpdateLineMetrics () from /usr/local/lib/libtk8.5.so
#9  0xb7fa6351 in AsyncUpdateLineMetrics () from /usr/local/lib/libtk8.5.so
#10 0xb7ecedb5 in TimerHandlerEventProc () from /usr/local/lib/libtcl8.5.so
#11 0xb7eb7e28 in Tcl_ServiceEvent () from /usr/local/lib/libtcl8.5.so
#12 0xb7eb80d6 in Tcl_DoOneEvent () from /usr/local/lib/libtcl8.5.so
#13 0xb7e89e4c in Tcl_VwaitObjCmd () from /usr/local/lib/libtcl8.5.so
#14 0xb7e5cd47 in TclEvalObjvInternal () from /usr/local/lib/libtcl8.5.so
#15 0xb7e5d44b in Tcl_EvalEx () from /usr/local/lib/libtcl8.5.so
#16 0xb7ea94b8 in Tcl_FSEvalFileEx () from /usr/local/lib/libtcl8.5.so
#17 0xb7f3aeba in Tk_MainEx () from /usr/local/lib/libtk8.5.so
#18 0x0804888c in main ()
```

As you may expect, it is possible to prevent such a segfault by disabling xft support when compiling tk. Although this is far from ideal, it's probably useful info. Having said that, the error doesn't have to be in libxft itself.

---

### Post by thagame on 2005-07-11
check and see if theres any broken packages. or if you compiled something that is in repos. and as far as gaim being a "hunk of junk" im guessing not so much considering it works and amsn dont :)

---

### Post by FishFace on 2005-07-11
No broken packages, and I haven't compiled stuff from source for ages, bar tk8.5 which I had anyway (and tried upgrading in an attempt to solve this) I've managed to run with tk8.4, which doesn't have xft support anyway (by the way, xft support means antialiased fonts) so it's no better

And as for gaim, well... Since amsn has the option of working (i.e. before whatever it was made it stop) and gaim doesn't have the option of not sucking - in the form of custom emoticons, general UI layout, weird handling of things like tabs, requirement of guifications to get popups, and a thousand little niggles... I'd say aMSN was still better! Plus I've now realised I can get it working without AA, so it's less of a death-by-gaim more of a torture-by-ugly-text scenario.

Still, same solutions, I expect :/ or getting tk8.4 to use AA.

---

