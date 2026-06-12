---
title: "Java EE 5 SDK installation"
date: 2006-07-01
forum: General Help
---

### Post by AlliumPorrum on 2006-07-01
Hi!

I just installed Java 5 EE SDK from the .bin, but still when I run 'java -version', it gives me this kind of version:

java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

What should I do to make the installed Java 5 to be the one that is executed??

---

### Post by bukwirm on 2006-07-01
Run 'sudo update-alternatives --config java' and select the appropriate option.

---

### Post by AlliumPorrum on 2006-07-01
I tried that, but for some reason it does not show the JDK that I just installed, only these:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java

My JDK EE 5 is installed on the default installation directory '/home/jasurakk/SUNWappserver/jdk'. What's wrong??

---

### Post by AlliumPorrum on 2006-07-01
Hey, now I noticed that the installation did not add the JDK 5's installation directory to the path, so that's the problem. Stupid installation set...:roll:

I have tried for a half an hour to find out how can I set the PATH variable in Ubuntu, but twithout any luck... So could some one please tell me how can I do it???

---

