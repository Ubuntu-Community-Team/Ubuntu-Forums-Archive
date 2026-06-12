---
title: "Eclipse does not load - looking for java in the wrong place?"
date: 2006-11-21
forum: General Help
---

### Post by Dual Cortex on 2006-11-21
The following happens when trying to run eclipse:

```
felipe@LinuxDesktop:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...not found
  testing /usr/lib/j2sdk1.5-ibm...not found
  testing /usr/lib/j2sdk1.4-ibm...not found
  testing /usr/lib/j2sdk1.5-sun...not found
  testing /usr/lib/j2sdk1.4-sun...not found
felipe@LinuxDesktop:~$ 

```

Now, using the following _does_ work ```
felipe@LinuxDesktop:~$ /usr/lib/eclipse/eclipse

``` 


And I believe I have Java 1.5 v9 installed: 
```
felipe@LinuxDesktop:~$ java -version
java version "1.5.0_09"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_09-b03)
Java HotSpot(TM) Client VM (build 1.5.0_09-b03, mixed mode, sharing)
felipe@LinuxDesktop:~$ 
```

Any ideas on how to get Eclipse working as it's *supposed* to?
It seems like eclipse is looking for java in wrong places?
Thanks in advance!

---

### Post by DaveBorealis on 2006-11-21
One possibility is to make a link from one of the paths in which eclipse is looking to where it actually is.

Dave

---

### Post by hod139 on 2006-11-21
maybe my [howto]("http://ubuntuforums.org/showthread.php?t=201378") will help?

---

