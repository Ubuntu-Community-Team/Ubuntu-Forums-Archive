---
title: "Eclipse/Java Super Slow in 8.04"
date: 2008-05-08
forum: General Help
---

### Post by Cerin on 2008-05-08
Just did a fresh install of Ubuntu 8.04, and everything in Eclipse takes forever. Eclipse will consume 100% CPU for 30 seconds for simple things like opening a file. I'm coming from Fedora, and I've never experienced such horrible performance with Eclipse before. Is this normal?

---

### Post by bilbo.san on 2008-05-08
I do not know much... but I have been searching for info on installing Eclipse as I want to use APTANA... and I think that you need to install Java JRE in order to make it work properly.
Hope this helps you.

b.

---

### Post by Cerin on 2008-05-08
Just tried using sun-java, and performance is no better.

---

### Post by rickh57 on 2008-05-08
I've not seen any symptoms like that with 8.04, both as the native OS on an old P4 and in a VMWare image. I'm using Sun's Java in both places, though.

---

### Post by Greg K on 2008-10-20
I've got the same thing. It wasn't always like this though, it's since I pulled down a Sun Java update on Sunday 12th Oct. That latest update has boned my Eclipse.

Initially I thought it might be Eclipse, so I updated all my components but it didn't help with performance. So I just tried switching from Eclipse 3.4 with PHP Eclipse to PDT 1.0.3 on Eclipse 3.3 and the performance is still terrible.

---

### Post by Paul41 on 2008-10-20
I don't know if anything in here will help but maybe...

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by Greg K on 2008-10-20
I ended up removing Java 6 (JRE, JDK and Browser Plugin) using synaptic, re-installing it through Add / Remove. Removing Eclipse completely. Then following the instructions on installation again.

This has improved things, though I'm yet to give it a proper test run. I'll know tomorrow. So far it looks like the possible update that occured some weeks ago might have changed my JVM set up with Sun's Java not being listed at the top.

Eclipse seemed to be using GCJ which would explain the performance issues (may be stability too).

[See here for instructions on getting Eclipse to use Sun's Java]("http://ubuntuforums.org/showthread.php?t=201378").

---

