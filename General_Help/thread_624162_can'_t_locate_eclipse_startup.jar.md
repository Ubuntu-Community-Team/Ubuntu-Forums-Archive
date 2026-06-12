---
title: "can' t locate eclipse startup.jar"
date: 2007-11-26
forum: General Help
---

### Post by mylesorme on 2007-11-26
I have installed eclipse from the ubuntu repository and have Sun's JDK 1.6 installed. 

At one time everything was working nicely but since uninstalling and reinstalling I'm having problems on startup. Instead of the splash screen I get the message at the bottom of this post which shows java-6-sun is being used

However...

I am unable to locate startup.jar 

locate is working fine (tested by locating known-to exist files)

Could this be as simple as getting hold of a copy of startup.jar and putting it in the right place?

If so, where can I get it from and where do i put it? - if I simply copy it to /usr/lib/eclipse/ will I have problems with updates?

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
-exitdata 8b8011
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar

---

