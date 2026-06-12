---
title: "confuesed about Java"
date: 2012-11-23
forum: General Help
---

### Post by thorbs on 2012-11-23
I was trying to solve a bug and as far as I understand I need to make a direct refference to what JRE I am using. But when I went into /usr/lib/jvm there seemed to be many different kinds of Java. Why are there so many and which one am I using?

---

### Post by steeldriver on 2012-11-24
If you have multiple java packages installed, iirc you should be able to view / select which one is in use by

```
sudo update-alternatives --config java
```for the jre / jvm, and

```
sudo update-alternatives --config javac
```for the jdk

Hope this helps

---

