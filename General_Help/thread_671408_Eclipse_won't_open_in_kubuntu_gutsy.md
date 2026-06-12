---
title: "Eclipse won't open in kubuntu gutsy?"
date: 2008-01-18
forum: General Help
---

### Post by zivxx on 2008-01-18
hey everyone...everytime i run my eclipse i get this error:
JVM terminated. Exit code=1
/usr/lib/jvm/java-6-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 4d0000
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 


anyone have an idea what it tells?
p.s.
i don't know if its for this forum but does eclipse come with a built-in C# plugin or i have to download it, if i need to download...how?

thanks very much for anyone who can help.

---

### Post by luisromangz on 2008-01-18
How have you installed Eclipse? From the repositories? If you didn't install the version from the repositories there is a very big chance that your system lacks some libraries that Eclipse needs.

Also, to develop C# applications, you should use Monodevelop, not Eclipse.

---

### Post by zivxx on 2008-01-18
i got monodevolp but my cousing told me to try and get eclipse, and yes i got it from the adpet manager but still won't run

---

### Post by oscarsfriend on 2008-01-18
Lots of people here are reporting that eclipse is not working after installing an xorg update, which breaks java (and hence eclipse).  Could this be the same problem? See here: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969) and here: [http://ubuntuforums.org/showthread.php?t=671020](http://ubuntuforums.org/showthread.php?t=671020)

---

