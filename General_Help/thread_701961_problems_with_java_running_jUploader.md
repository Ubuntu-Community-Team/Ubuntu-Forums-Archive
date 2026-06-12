---
title: "problems with java running jUploader"
date: 2008-02-19
forum: General Help
---

### Post by guine on 2008-02-19
Im trying to run jUploader but whenever I try to start it I get
```
Starting JUploadr...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
GCJ is an incompatible version of java
Download the official version at http://java.sun.com
```
Ive tried installing a bunch of the gcj and java packages from synaptic but none of them seem to have any effect.  Do I need to get a newer version of java, and if so is it possible to get through synaptic or do I have to manually install it?
Thanks

---

### Post by openguru on 2008-04-26
All you need to do is, install Sun java and reconfigure the java version to use.

sudo update-alternatives --config java

should do it..

---

