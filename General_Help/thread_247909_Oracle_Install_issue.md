---
title: "Oracle Install issue"
date: 2006-08-31
forum: General Help
---

### Post by jhandloff on 2006-08-31
Hello
I've been banging my head against this all day.
I'm trying to get Oracle 10g installed and I keep running into 
> Exception in thread "main" java.lang.UnsatisfiedLinkError: /tmp/OraInstall2006-08-31_10-41-34AM/jre/1.4.2/lib/i386/libawt.so: libXtst.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)


I'd gotten similar errors before and just apt-get install the package.  When I try it on this one, I get:
> joel@legba:/orinst/database$ sudo apt-get install libXtst
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libXtst


Note that I also went through installing Java today (also rather confusing, but I think thats my fault for going to the wrong HowTo)

Anyhow, help is appreciated!!
-joel

---

### Post by N6546R on 2006-08-31
Try 

apt-get install libxtst6

Perry

---

### Post by jhandloff on 2006-08-31
thanks kindly!
(thats the problem with case-sensitivity...)

---

