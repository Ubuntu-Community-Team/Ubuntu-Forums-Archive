---
title: "Eclipse crashes when launched - Fiesty"
date: 2007-09-02
forum: General Help
---

### Post by dnalbach on 2007-09-02
When I try to start Eclipse on a fairly clean Fiesty install, it crashes immediately. I tried starting it as sudo from a shell and got the following error:

searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found
/usr/lib/jvm/java-gcj/bin/java: symbol lookup error: /usr/lib/../lib/libgcj.so.70: undefined symbol: 



I don't know how to fix this. I've uninstalled and reinstalled Eclipse and all it's dependencies in Synaptic, but that didn't make any difference.

Ideas?

---

### Post by tzulberti on 2007-09-02
The problem is that Eclipse is using ecj as default... I think that you should change the file /etc/ecplise/java_home to something like this:
/usr/lib/jvm/java-1.5.0-sun <-- The jvm thar you are using
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

That worked for me...

---

