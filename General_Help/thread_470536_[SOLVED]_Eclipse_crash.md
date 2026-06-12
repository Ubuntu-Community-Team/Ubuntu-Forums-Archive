---
title: "[SOLVED] Eclipse crash"
date: 2007-06-11
forum: General Help
---

### Post by borobudur on 2007-06-11
Hi there, 
I'm using Eclipse on Ubuntu 6.10. I have the problem that it crashes all the time after a while being started up.
Eclipse shows this message:
```
JVM terminated. Exit code=1
/usr/lib/jvm/java-1.5.0-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 1c0011
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-1.5.0-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 
```
What could that be?

---

### Post by borobudur on 2007-06-15
Found the problem!

It was the php plugin: the preview browser makes trouble there...

---

### Post by Staach on 2007-08-14
I am having the same problem (it seems.)  You say it was the php plugin that gave  you the problem, can you tell me how you fixed it then? Did you reinstall the PHPeclipse again or something else?

Cheers
Staach

---

### Post by Bobbafett on 2007-08-15
Did anyone found how to effectively solve this problem?

I am running Ubuntu 6.10, Java 1.6.0, Eclipse 3.2.1, and PHPEclipse plugin. And like stated before PHPEclipse's PHP Browser seems to be the problem. Every time a file is saved and the PHP Browser tries to update its view the whole Eclipse  crashes.

I went to Window->Preferences->PHPEclipse->Browser Preview and just unchecked the two options there: "Refresh PHP browser" and "Show PHP browser" and that seems to solve the problem at least for now.

But, what about if I do want to make the PHP Browser to work without crashing Eclipse? what needs to be properly configured?

Thanks a lot

---

### Post by borobudur on 2007-08-18
That was my solution too to uncheck those options in the preferences.
For me it's fine like that, I check my work directly in the browser.

---

