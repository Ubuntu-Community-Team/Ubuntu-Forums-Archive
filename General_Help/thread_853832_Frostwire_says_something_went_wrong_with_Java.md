---
title: "Frostwire says something went wrong with Java?"
date: 2008-07-08
forum: General Help
---

### Post by zackf on 2008-07-08
I installed sun java via ```
sudo apt-get install sun-java6-jdk
``` and then ran ```
sudo update-java-alternatives -s java-6-sun
``` and then installed frostwire. However, when I try to run frostwire I get this:
```

Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
```

So it looks to me like it's seeing I have Java 1.6.0_03. So what's up daggone it?

---

### Post by Car60n on 2008-07-08
try changing the java version
```
update-alternatives --config java
```

---

### Post by zackf on 2008-07-08
Sun was my only option for that one. What's weird is that Limewire works fine.

---

### Post by Car60n on 2008-07-08
Might not help much but you could try to re-install frostwire...

---

