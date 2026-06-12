---
title: "after a did a: &quot;kill PID&quot; =&gt; my eclipse crashes when try to make a  project target"
date: 2007-10-18
forum: General Help
---

### Post by sidatra7 on 2007-10-18
Hallo everybody, 

I tried today to "make" a project target using eclipse. Because eclipse freezed for about 1 hour and I couldnt terminate it properly, I gave the following command in terminal:

> top

and found out that one process of java with the pid 7504 was using all of my pc s memory.
Therefore I then typed in the terminal the following command:

> kill 7504

So far everything looked OK, because eclipse finally terminated.
But later on when i restarted eclipse, it crashed after some minutes.
I rebooted, and the problem continues till now.
The error code i get is the following:
> 
JVM terminated. Exit code=1
/usr/lib/jvm/java-1.5. 0-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=nev er
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 261b800c
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-1.5.0-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=nev er
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar

I'read another post 
> [http://ubuntuforums.org/showthread.php?t=436316&highlight=jvm+terminated.+exit+code%3D1](http://ubuntuforums.org/showthread.php?t=436316&highlight=jvm+terminated.+exit+code%3D1)
where another user had the same error output but no real solution was posted thr whatsoever.
So I hope that maybe the more experienced users on linux can help a newbie like myself.

Thanks in advance :guitar:

---

