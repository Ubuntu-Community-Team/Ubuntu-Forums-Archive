---
title: "Problems starting ArcExplorer"
date: 2007-06-27
forum: General Help
---

### Post by R.E.B.S. on 2007-06-27
Hello,

I just installed ArcExplorer on Feisty. Everything worked fine. But when I try to start ArcExplorer using the command "aejava" I receive the following error message:

Exception in thread "main" java.lang.NoClassDefFoundError: com/esri/ae/AE

Has anyone some idea, how to fix this? There is a thread in the forum where someone already had this problem and actually fixed it, but unfortunately he (or she) didn't tell how he did it...

Thanks,
R.E.B.S.

---

### Post by blue_bullet on 2008-07-22
> **R.E.B.S. said:**
> Hello,

I just installed ArcExplorer on Feisty. Everything worked fine. But when I try to start ArcExplorer using the command "aejava" I receive the following error message:

Exception in thread "main" java.lang.NoClassDefFoundError: com/esri/ae/AE

Has anyone some idea, how to fix this? There is a thread in the forum where someone already had this problem and actually fixed it, but unfortunately he (or she) didn't tell how he did it...

Thanks,
R.E.B.S.

Here over a year later I have the same problem.  Can anyone provide some help here?
This is freeware competing with ESRI's own commercial software so they are not inclined to assist people using the freeware.  They want money.  Here's what I get when I try to run ArcExplorer 9.3 from Terminal.  I am running Hardy Heron. 

rob@fargo:~$ tcsh -l 
fargo:~> aejava
Exception in thread "main" java.lang.NoClassDefFoundError: com/esri/ae/AE
Caused by: java.lang.ClassNotFoundException: com.esri.ae.AE
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
fargo:~>

---

