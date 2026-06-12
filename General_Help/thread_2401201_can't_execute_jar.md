---
title: "can't execute jar"
date: 2018-09-14
forum: General Help
---

### Post by Kris_M on 2018-09-14
18.04.1
have
```
kris@deepthought4L:~$ java -version
openjdk version "10.0.2" 2018-07-17
OpenJDK Runtime Environment (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.2)
OpenJDK 64-Bit Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.2, mixed mode)
kris@deepthought4L
```

can
```
kris@deepthought4L:~/myjava$ javac Hello.java
kris@deepthought4L:~/myjava$ java Hello
Hello, world from Ubuntu!
kris@deepthought4L:~/myjava
```

have jar for looking at android logcat that works on win7. LogcatOfflineViewer_20120505.jar
can right click on it and get offered open with OpenJDK java 11 runtime. click on it but nothing happens. zero, nada. <-- says 11, above says 10
I watch processes but see nothing.
ideas?
Thanks!!!

edit: I used synaptic to remove 11 and add 8 but no change.
I moved file from ntfs to home but no change (is x)

edit2: I d/l it again to home, extracted it, tried to execute, said it wasn't ex, set to ex, again nothing.

Maybe this can only be run under windows... ?

---

### Post by Kris_M on 2018-09-14
aha
```
kris@deepthought4L:~/Downloads/logcatofflineviewer$ java -jar LogcatOfflineViewer_20120505.jar
Exception in thread "main" java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:498)
    at org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader.main(JarRsrcLoader.java:58)
Caused by: java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
    at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
    at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
    at org.eclipse.swt.internal.C.<clinit>(Unknown Source)
    at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
    at com.logcat.offline.UIThread.runUI(UIThread.java:112)
    at com.logcat.offline.Main.main(Main.java:6)
    ... 5 more
kris@deepthought4L:~/Downloads/logcatofflineviewer$ 

```

So it's saying my 8 is 64bit. I looked in synaptic and don't see any offering for 32bit (or 64bit for that matter...) How would I change it to 32bit?

---

### Post by Kris_M on 2018-09-14
so I dl jre-8u181-linux-i586.tar.gz and in /usr/share/java I did tar zxvf jre-8u73-linux-i586.tar.gz
but it doesn't recognize the new java when i right click on a jar.

---

### Post by Holger_Gehrke on 2018-09-15
That won't work, even if you somehow get the 32-bit Java to run. The offending 32-bit library is the Standard Widget Toolkit (swt), a graphics and UI library that uses JNI (Java Native Method Invocation) to call the OS to produce whatever widgets the program needs for it's UI. You need a 64-bit swt.jar for Linux - or more specifically for GTK+  - and you need to change the jar to load that instead of the included, Windows-specific swt.jar.

Holger

---

### Post by Kris_M on 2018-09-15
> **Holger_Gehrke said:**
> That won't work, even if you somehow get the 32-bit Java to run. The offending 32-bit library is the Standard Widget Toolkit (swt), a graphics and UI library that uses JNI (Java Native Method Invocation) to call the OS to produce whatever widgets the program needs for it's UI. You need a 64-bit swt.jar for Linux - or more specifically for GTK+  - and you need to change the jar to load that instead of the included, Windows-specific swt.jar.

Holger

Thanks!

---

