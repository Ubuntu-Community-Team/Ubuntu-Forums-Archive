---
title: "Sun Java installed but no java executable"
date: 2008-06-19
forum: General Help
---

### Post by tim1 on 2008-06-19
I have sun-java6-bin/jre installed through synaptic but somehow I don't have a java executable.

When I try to select a Java VM with update alternatives I get this:

```
$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
```

But when I try to run Java I get this:

```
$ java
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
```

Any suggestions?

---

### Post by phidia on 2008-06-19
Open the package manager and search for java or sdk-since I think you want the sdk.
There should be a package there called sun-java6-sdk you can also use apt-get.
If you want the java builder you want the sdk.

---

### Post by tim1 on 2008-06-19
Do you mean the JDK?

But that's the development kit. I just want to run apps.

---

### Post by phidia on 2008-06-19
> **tim1 said:**
> Do you mean the JDK?

But that's the development kit. I just want to run apps.

Sorry and it is listed as sdk in synaptic, but anyway try [URL="http://ubuntuforums.org/showthread.php?t=760816&highlight=installing+java"]this thread
[/URL] and see if that helps.

---

