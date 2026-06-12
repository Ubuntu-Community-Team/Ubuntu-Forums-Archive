---
title: "[SOLVED] Modifying Eclipse Path"
date: 2008-06-20
forum: General Help
---

### Post by lost09 on 2008-06-20
I have the latest JDK installed on Hardy, but Eclipse is still using the outdated version. How do I update the path so that Eclipse uses the new java compiler?

---

### Post by Nepherte on 2008-06-20
```
sudo update-alternatives --config java
```
and then you enter the number of the java version you want to use.

---

### Post by lost09 on 2008-06-20
Hmm... apparently the latest version is already selected. 

My computer professor suggested that as the problem when Eclipse appeared not to support generic types (it underlines them in red and fails to compile). However, I clicked on the error tag and was given something about "will only work if java version is 5" (or something to that effect). By accidentally tapping the mousepad too hard, I discovered one can in fact change the java version from 1.6.0_06 to the (I'm assuming) less advanced version that eclipse wants. Voila, it works, but now my question is, why?

---

### Post by jamesstansell on 2008-06-21
Eclipse has several places to choose which JVM to use.  One is for starting the IDE, and one is for building projects and another is for running projects.  They can all be configured in multiple places. (And generally the "update alternatives" methods don't apply.)

That said, I remember using Java 6 with eclipse over a year ago.  What version do you have installed?  How did you install it?  Are you running Hardy as 32bit or 64bit?

---

### Post by Nepherte on 2008-06-21
You can also modify in what order eclipse searches for JVMs. Open up /etc/eclipse/java_home:
```
gksudo /etc/eclipse/java_home
```
and place the jvm you want as the first one.

You should also be able to override this setting per user in ~/.eclipse/eclipserc. That is completely up to you.

---

### Post by lost09 on 2008-06-21
My thanks to the both of you; it seems to be working now.

---

