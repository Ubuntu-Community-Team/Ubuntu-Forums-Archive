---
title: "JAVA related"
date: 2007-08-13
forum: General Help
---

### Post by jfg69 on 2007-08-13
If I disable GNU version of Java and use the Sun version instead, are there any packages or anything else that is going to fail? Is the "ubuntu" version of JVM very different from the Sun version?

---

### Post by qamelian on 2007-08-13
Anything that works with the GNU version of Java should work fine with Sun's official Java. If you're worried about compatibilty issues, you can have multiplle Java virtual machines installed and use whiever one is necessary for a particular app. Personally, I always install the newest Sun Java VM and set it as my default. I haven't had any problems by doing this and, in fact, this has corrected a few Java issues.

---

### Post by jfg69 on 2007-08-13
Excellent, thank you for the reply.

I havent seen any issues as of yet, but if I do I will post here. As I'm new to *nix, how can I tell if both are still installed? I ran java -version on terminal and only this is showing:

```

jerry@desktop:~$ java -version
java version "1.6.0_02"
Java(TM) SE Runtime Environment (build 1.6.0_02-b05)
Java HotSpot(TM) Client VM (build 1.6.0_02-b05, mixed mode, sharing)
jerry@desktop:~$ 

```

---

### Post by qamelian on 2007-08-13
> **jfg69 said:**
> Excellent, thank you for the reply.

I havent seen any issues as of yet, but if I do I will post here. As I'm new to *nix, how can I tell if both are still installed? I ran java -version on terminal and only this is showing:

```

jerry@desktop:~$ java -version
java version "1.6.0_02"
Java(TM) SE Runtime Environment (build 1.6.0_02-b05)
Java HotSpot(TM) Client VM (build 1.6.0_02-b05, mixed mode, sharing)
jerry@desktop:~$ 

```

In a terminal, type:
```
cat /etc/jvm
```
This will display any Java VMs installed and the order in which your system will search them. For example, on my Gutsy box, I get:
```
carl@arkham:~$ cat /etc/jvm
# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.


/usr/lib/jvm/java-6-sun-1.6.0.02
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr

```


Note that some apps use their own config file to manage this as well. Eclipse, for example, has a separate config at /etc/eclipse/java_home that determines which jvm it will try to use.

---

