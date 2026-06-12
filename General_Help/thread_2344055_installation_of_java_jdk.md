---
title: "installation of java jdk"
date: 2016-11-22
forum: General Help
---

### Post by rupak04 on 2016-11-22
Hello, 
I am not sure whether java is installed in my system or not. Please help. I am a beginner to ubuntu.

I have executed following command on my terminal:
rupak@rupak-ThinkPad:~$ java -version

result is:
openjdk version "1.8.0_111"
OpenJDK Runtime Environment (build 1.8.0_111-8u111-b14-2ubuntu0.16.04.2-b14)
OpenJDK 64-Bit Server VM (build 25.111-b14, mixed mode)

---

### Post by howefield on 2016-11-22
Looks like you have the open source implementation of the java jdk installed.

Try..

```
apt-cache policy openjdk-*
```

and browse the list, you'll see which package are installed and the package names.

What is making you ask the question, do you have a jave dependant application which isn't working ?

---

