---
title: "openjdk can't be used as the default application for jar files"
date: 2024-06-18
forum: General Help
---

### Post by lixiaolong2007726 on 2024-06-18
System:Ubuntu 24.04LTS (gnome)
After installing openjdk-21-jre via apt and rebooting, openjdk is not recognized as the default application, I tried to select open with but there is no openjdk in the directory

---

### Post by TheFu on 2024-06-18
JDK - Java Development Kit - is a group of libraries and development tools.
JRE - Java Runtime Environment - is where you'll find java and production runtime libraries - which are normally the programs a java developer would want to use. 
javac is the compiler.  
java is the java-bytecode-interpreter.

[https://www.javatpoint.com/simple-program-of-java](https://www.javatpoint.com/simple-program-of-java) explains how to create, compile and run a "hello world.java" program. Perhaps that would be helpful?

If you are seeking an IDE, that isn't in those tools/packages.  On Unix-like OSes, IDEs typically aren't used. We use different terminal windows for different needs.  I generally have 4 terminal windows open.
[LIST]
[*]Editor ( I use vim)
[*]Small compile window using make/ant/ or a custom compile script
[*]Debugger (since I'm not a java programmer, I don't know what the typical debugger is, but for C/C++, it would be gdb)
[*]Documentation lookup terminal - manpages for the different stuff.
[/LIST]
Of course, every programmer has their own preferences and many environments will be very restrictive, not allowing any internet access.

If you are looking for an IDE, there are a few. Most are extremely bloated, slow, and painful to use unless your workstation has 32GB of RAM or more, a recent Core i7 CPU, and fast NVMe SSD.  Eclipse and NetBeans are two java IDEs that even I've heard of.  In Ubuntu, both appear to be snap packages", which can bring some undesirable restrictions.  That's the good and bad part of snap packages.  I'm not a fan of snap packages, but in the Ubuntu ecosystem, they are hard to avoid without some extra work.  For many people, the easiest way to avoid snaps, but retain the ease of Ubuntu is to choose Linux Mint or Debian desktop.

---

