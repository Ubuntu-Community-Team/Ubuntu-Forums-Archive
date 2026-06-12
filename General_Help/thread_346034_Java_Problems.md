---
title: "Java Problems"
date: 2007-01-25
forum: General Help
---

### Post by willbur on 2007-01-25
I'm trying to install Jose on my Ubuntu (6.10) installation. java -version reports: 
 
java version "1.4.2" 
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7) 
 
If I run java ~/jose/jose.jar from the command line, I get: 
 
Exception in thread "main" java.lang.NoClassDefFoundError: .home.willbur.jose.jose.jar 
at gnu.java.lang.MainThread.run(libgcj.so.70) 
Caused by: java.lang.ClassNotFoundException: .home.willbur.jose.jose.jar not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}} 
at java.net.URLClassLoader.findClass(libgcj.so.70) 
at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70) 
at java.lang.ClassLoader.loadClass(libgcj.so.70) 
at java.lang.ClassLoader.loadClass(libgcj.so.70) 
at gnu.java.lang.MainThread.run(libgcj.so.70) 
 
If I run java -jar jose.jar I get: 
 
Failed to load Main-Class manifest attribute from jose.jar 
 
I'm clearly a Linux newbie in need of some help :-k

---

### Post by willbur on 2007-01-25
Sorry, everyone - I should have said that Jose is a java based chess program which requires java 1.4 to run....

---

### Post by Ramses de Norre on 2007-01-25
Seems more like a compatibility problem with gcj and .jar, why don't you try sun's java? All java versions are backwards compatible with older versions.

---

### Post by willbur on 2007-01-25
Thanks, Ramses. There is an option to download the .zip complete with it's own Java included, but I get the same result. Did I mention I was a newbie? Please bear this in mind ;)

---

### Post by Ramses de Norre on 2007-01-25
Ok, I suggest you install sun's java 5:```
sudo aptitude install sun-java5-bin sun-java5-jre
sudo update-java-alternatives -s java-1.5.0-sun
```
Then try running the app again.

---

### Post by bmonkey on 2007-01-25
"Exception in thread "main" java.lang.NoClassDefFoundError: .home.willbur.jose.jose.jar "

Basically that means that the JAR was compliled with no main class in it, or it was just not complied properly, try find another version, or open the jar and see what is set for Main-Class in the MANIFEST.MF file?

---

### Post by willbur on 2007-01-26
Many thanks, everyone - I'll try it again this weekend...

---

