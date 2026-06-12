---
title: "Kubuntu Java Problem"
date: 2006-11-15
forum: General Help
---

### Post by TommyMann on 2006-11-15
Firefox is not acting java friendly. I looked up solutions on the forum and tried the one that most people were having success with. I downloaded sun-java from synaptic, but I get this error:

> tommymann@tommymann-laptop:~$ update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
update-alternatives: unable to make /etc/alternatives/java.dpkg-tmp a symlink to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java: Permission denied

Anyone know what to do in this case. I would really like Java to work.
And if in your benevolence you decide to help more, could you tell me how to get flash 9 on here too.

-Tommy

---

### Post by Brainjar on 2006-11-18
I've the same problem. Have you find out any solution ?

---

### Post by taurus on 2006-11-18
You need to run that command as root!!!

```
sudo update-alternatives --config java
```

---

### Post by Brainjar on 2006-11-19
Thanks taurus !!
It works fine !!!
 
I've resolved a big problem with your precious help.
:D

---

