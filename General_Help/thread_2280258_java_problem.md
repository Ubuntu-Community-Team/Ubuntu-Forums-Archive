---
title: "java problem?"
date: 2015-05-29
forum: General Help
---

### Post by aidas2 on 2015-05-29
Hello guys
In my free time i like to play runescape private server.

```

java -jar client.jar

```

That's how i try to open the server

and in terminal i get error;

> 
Exception in thread "main" java.lang.UnsupportedClassVersionError: Launcher : Unsupported major.minor version 52.0


i changed my jdk from 6 to 8 (still same error), changing to 7 i get same error

```

java -veresion

```

> 
java version "1.6.0_35"
OpenJDK Runtime Environment (IcedTea6 1.13.7) (6b35-1.13.7-1ubuntu0.14.04.1)
OpenJDK 64-Bit Server VM (build 23.25-b01, mixed mode)


```

javac -version

```

> 
javac 1.6.0_35


So i changed my jdk versions and i got same error so i don't think that problem is with java. What can cause this error if not java?

---

### Post by efflandt on 2015-05-29
It is not clear how or what you are installing or uninstalling. Obviously you still have openjdk-6 installed (apparently your default java). And I don't think there is an openjdk-8 yet (at least not in normal 14.04 repos). I have not used Oracle Java since it has no longer been mainstream in Ubuntu, but openjdk-7-jre has worked for everything I do with java (just minecraft and related modpacks). If you properly removed openjdk-6 and had openjdk-7-jre installed it would look like this:```
dpkg-query -l openjdk* | grep ii
ii  openjdk-7-jre:amd64                                   7u79-2.5.5-0ubuntu0.14.04.2                            amd64        OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless:amd64                          7u79-2.5.5-0ubuntu0.14.04.2                            amd64        OpenJDK Java runtime, using Hotspot JIT (headless)

java -version
java version "1.7.0_79"
OpenJDK Runtime Environment (IcedTea 2.5.5) (7u79-2.5.5-0ubuntu0.14.04.2)
OpenJDK 64-Bit Server VM (build 24.79-b02, mixed mode)
```

---

### Post by monkeybrain20122 on 2015-05-30
Get openjdk-8 from [https://launchpad.net/~paulo-matias/+archive/ubuntu/openjdk-lts-backports](https://launchpad.net/~paulo-matias/+archive/ubuntu/openjdk-lts-backports)
Then you need to make it the default
[http://askubuntu.com/questions/159575/how-do-i-make-java-default-to-a-manually-installed-jre-jdk](http://askubuntu.com/questions/159575/how-do-i-make-java-default-to-a-manually-installed-jre-jdk)

---

