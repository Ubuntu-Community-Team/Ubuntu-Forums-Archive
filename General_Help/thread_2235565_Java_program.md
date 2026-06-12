---
title: "Java program"
date: 2014-07-21
forum: General Help
---

### Post by CVGH on 2014-07-21
Hi!

I'm trying to run this Java program:

[https://mediaserver.thinkorswim.com/installer/install.html](https://mediaserver.thinkorswim.com/installer/install.html)

It is a program for trading the markets.

Hangs on start most times, locks desktop. I need to go to the virtual terminals to kill Java.
Sometimes it starts fine but once in the program, it takes a while for the clicks
on elements to be correct. They are off by some pixels.

What should I be looking for as TD Ameritrade is clueless...............


:~/thinkorswim$ java -version
java version "1.7.0_65"
Java(TM) SE Runtime Environment (build 1.7.0_65-b17)
Java HotSpot(TM) 64-Bit Server VM (build 24.65-b04, mixed mode)

AMD A8 12MB Dell Laptop running Ubuntu 14.04

Thanks!

---

### Post by grier-devon on 2014-07-21
I would try upgrading to Java 1.8 and see if that fixes it. Otherwise it might be the application.

---

### Post by CVGH on 2014-07-22
Gave that a shot but program just hangs, never starts.....

---

### Post by CVGH on 2014-09-13
I think Unity was the problem. Logging out and running KDE seemed to have fixed the problem.

---

