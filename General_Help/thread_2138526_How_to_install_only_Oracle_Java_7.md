---
title: "How to install only Oracle Java 7?"
date: 2013-04-24
forum: General Help
---

### Post by ubunet on 2013-04-24
Hi,

I installed **Oracle Java 7 JRE** from package of site. I try to remove openjdk7 but Xubuntu 12.10 x32 tries to install **gcj** (gcj-4.7-base gcj-4.7-jre gcj-4.7-jre-headless gcj-4.7-jre-lib gcj-jre gcj-jre-headless libgcj-common libgcj13 libgcj13-awt). 

What I need to do to stay only with Oracle **JRE** without install any other packages?

---

### Post by ubunet on 2013-04-24
First, installing Oracle Java 7 from PPA of webupd8. After this remove all **OTHER** java jre/jdk (oracle **manual** installed and openjdk).
```
sudo apt-get purge openjdk-7-jre*
```
Instructions to install Oracle Java 7 from PPA here: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by QIII on 2013-04-24
Hello.

If you try to uninstall OpenJDK, you are bound to get dependency issues.  Don't bother trying to do it.

Just use the webupd8 PPA to install Oracle Java 7.  It will set Oracle Java 7 as your alternative automatically.

OpenJDK 7 can exist on the machine happily with Oracle Java 7 and it will be doing nothing more than being on your disk.  It will not run or consume resources.  It won't compete with Oracle Java 7 or confuse anything.

Have a read through the Java wiki link in my signature.  I've put a bit in there about how to switch between OpenJDK 7 and Oracle Java 7 should you choose to.

Best wishes.

---

