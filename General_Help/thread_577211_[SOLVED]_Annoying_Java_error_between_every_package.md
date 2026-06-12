---
title: "[SOLVED] Annoying Java error between every package configuration"
date: 2007-10-16
forum: General Help
---

### Post by YAOMTC on 2007-10-16
Every time a package is configured/uninstalled, it seems as if Java wants to reinstall itself or something. Between each instance, I need to abort Java's (documentation?) installation.

E: sun-java6-doc: subprocess post-installation script killed by signal (Interrupt)

I've seen other threads about this, but not with Java 6, and none with an answer that I've seen. Is there a solution for this?

**EDIT:** I've put jdk-6-doc.zip into /tmp, as well as the 'doc' folder unpacked from another copy of that file (I didn't know which to do, so I did both). This seems to have solved the problem. (See the post at the bottom of this page.)

---

### Post by YAOMTC on 2007-10-16
Time to move it up.

---

### Post by lynxus on 2007-10-16
Have you tried just installing java manually correctly . and then does it keep trying?

---

### Post by YAOMTC on 2007-10-16
This started happening just *after* I installed Java manually and correctly.

---

### Post by YAOMTC on 2007-10-17
Time to move it up.

---

### Post by YAOMTC on 2007-10-21
Time to move it up.

---

### Post by YAOMTC on 2007-10-23
Man, this is definitely the most annoying software-related problem I've had in a long time.

---

### Post by YAOMTC on 2007-10-23
.

---

### Post by YAOMTC on 2007-10-23
.

---

### Post by smaller on 2007-10-23
Don't know if this is the answer to your problem or not. But the java documentation package is just a placeholder, see the following quote from the package description: 

> 
This package does not contain the Java Documentation
for the Java(TM) Development Kit (JDK).  The Java Documentation
(jdk-6-doc.zip) may be downloaded from
[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/) and, if placed
in /tmp (with root.root ownership), this package will
install the Java Documentation with the corresponding JDK.

Did you do this? I'm just guessing, but perhaps you didn't put the file there and the package is looking for it every time you run synaptic and consequently getting stuck every time...

---

### Post by YAOMTC on 2007-10-23
I set the Java installer to download it to /tmp and extract it... But I don't see it there.

---

### Post by YAOMTC on 2007-10-25
Solved! Thanks, Smaller!

---

