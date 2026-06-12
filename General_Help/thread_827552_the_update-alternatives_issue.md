---
title: "the update-alternatives issue"
date: 2008-06-12
forum: General Help
---

### Post by voltage on 2008-06-12
Dear all Expert,

may i know how to add or remove java alternatives link into my Ubuntu box.

* Ubuntu version - Ubuntu 8.04 LTS Server Edition
* Installed JDK version - Sun Java 6 (by using sudo apt-get install sun-java6-jdk)
* alternatives listing for java by using sudo update-alternatives --config java is /usr/lib/jvm/java-6-sun/jre/bin/java (but what is need is /usr/lib/jvm/java-6-sun/bin/java)

Please Advice, Thanks

---

### Post by mrsteveman1 on 2008-06-12
What is it that doesn't work?

As far as i know, the update-alternatives things just changes the location of certain java binaries (including java itself), as well as some of the libraries that come with it.

The java symlink itself is in /usr/bin i think, so if you have sun java installed at all java apps should work.

---

