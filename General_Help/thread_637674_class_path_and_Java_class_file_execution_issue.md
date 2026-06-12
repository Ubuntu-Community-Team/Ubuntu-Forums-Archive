---
title: "class path and Java class file execution issue"
date: 2007-12-11
forum: General Help
---

### Post by asif.kalim on 2007-12-11
i am facing 2 problems, and need to some information

1; i installed jdk 6 on ubuntu 6.10, when i set PATH variable, that is available for the current session only, when i open a new session of cosole, i lost the settings. I set path not from root and the variable value is
**export PATH=$PATH:/usr/local/jdk1.6.0_03/bin**

i want java and javac commands globally accessible for both of the users.

2; javac command works ok, and class file is created. when i run that class file using java command, bash gives following error
-------------------------------------------------------------------------------------------------------------------------------
Exception in thread "main" java.lang.ClassFormatError: WeLinux (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)
-------------------------------------------------------------------------------------------------------------------------------

Q- what is the difference between gij and gcj, do they have any conflict if i install java. 

Your answers will be of a great help,

Thanks,
asif

---

### Post by prince_niceguy on 2007-12-11
seems the jvm is not sun jvm..

to set your path permanently just include the export PATH line in the .bashrc in your home directory.

ensure it is set as export PATH=[java sun path]:$PATH.

this will make sure that the sun java takes precedence compared to other jvm.

---

