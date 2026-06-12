---
title: "java 6"
date: 2007-01-22
forum: General Help
---

### Post by mindworm on 2007-01-22
i just recently reinstalled ubuntu and im trying to install what used to be jre 5 update 10 but now its 6 and the commands are off and im having trouble doing it

fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin

sudo dpkg -i sun-j2re1.5_1.5.0+update10_i386.deb


now that its java six how would i change those to make sure the installation works

---

### Post by mindworm on 2007-01-22
anyone

---

### Post by NeoChaosX on 2007-01-22
The make-jpkg utility hasn't been updated for Java 6 yet, that's why it doesn't work. (And even it were, it probably only be uploaded to feisty.) Just download the sun-java6 debs from [this thread](http://www.ubuntuforums.org/showthread.php?t=325182).

---

