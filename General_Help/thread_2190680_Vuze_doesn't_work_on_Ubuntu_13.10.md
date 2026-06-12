---
title: "Vuze doesn't work on Ubuntu 13.10"
date: 2013-11-28
forum: General Help
---

### Post by frogwarrior on 2013-11-28
I installed Ubuntu 13.10, and now vuze won't work. When I start it up, it just loads this gray screen:
[IMG]http://gyazo.com/23ee314be5482ccc86613f8a68bbf39e.png[/IMG]

it looks like its crashed, but the terminal doesn't give any error messages or anything like that. Also, another problem is when I install vuze, it installs openJDK. I use oracle JDK, so when vuze installs openJDK, then openJDK becomes my default JDK. None of this happened with older versions of Ubuntu. Anyone know what the problem is here?

EDIT: I think the problem is java itself, when I go to the verify java page, I get the same blank gray screen where the applet should be:
[IMG]http://gyazo.com/0f41011868f42159b3964bdd826735fb.png[/IMG]
I installed java first with "sudo apt-get install oracle-java8-installer, but I just installed it manually from the tar archive and it still doesn't work. After removing openjdk (which uninstalled vuze in the process), heres what java -version says:
```
:~$ java -version
java version "1.7.0_45"
Java(TM) SE Runtime Environment (build 1.7.0_45-b18)
Java HotSpot(TM) Server VM (build 24.45-b08, mixed mode)

```

Anyone know how I can diagnose the problem here?

EDIT: I removed jdk 1.7, and installed (using oracle-java8-installer) jdk1.8 properly, now when I reinstalled vuze it didn't install openjdk, but vuze still isn't working, it still just shows a gray screen:
[IMG]http://gyazo.com/cc36b84a149497caf14d6b09544c5027.png[/IMG]

---

### Post by mikewhatever on 2013-11-29
What does 'jave -version' say now? Perhaps Vuze doesn't work with Java 8.

---

