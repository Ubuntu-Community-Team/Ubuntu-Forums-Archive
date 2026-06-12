---
title: "Eclipse Freezes/Slows down when I type &lt;&gt;"
date: 2007-02-01
forum: General Help
---

### Post by gazotem on 2007-02-01
System:
Gateway m680
ATI Mobility Radeon x700
1gb ram
Intel Pentium M 1.7


I am somewhat new to linux and programming.

While using Eclipse:

Version: 3.3.0
Build id: I20061214-1445

With the latest CDT plugin, I am working in a C++ perspective environment.  When I attempt to write < followed by > i.e. static_cast<int[COLOR="Red"]**>**[/COLOR] On the second > it will freeze up for about 2 - 3 minutes, then come back with the > inserted.

I am pretty sure I have updated my Java packages, although i do not know if this matters.

Thank you.

---

### Post by phossal on 2007-02-01
Which version of CDT? Why are you using an old build of eclipse? I'd recommend upgrading eclipse, CDT and Java (if you're not using JDK 6).

In addition, regardless of your platform, I would recommend the 32Bit options for both eclipse and Java. 

Per the CDT plugin page, the version of the plugin download is *heavily* tied to the version of eclipse.

---

### Post by gazotem on 2007-02-02
CDT Version 3.1.1,
I updated Java to JDK 6.

I tried a bunch of different builds of eclipse, and nothing changed.

It is a very odd problem, I can editing for an hour.  If there is for instance: cout << and i decide to type a > , it will freeze.  If there is not a << in the code, it will not freeze....


I want to assume that it is some type of shortcut, but I looked through all of them and did not find it.

---

### Post by kthakore on 2007-12-18
I have the exact same problem except I am making qt 4 application and eclispe freezes every two seconds. I mean so irritating.

---

### Post by gazotem on 2007-12-18
So I originally posted this problem.  Now since I have updated my Ubuntu and have the most recent install of Java it has not occurred and eclipse works well. I would recommend updating your JRE version to 1.6.x and then try eclipse again.

In the meantime, you can try to use Anjuta IDE which is suffice for the most part.

---

### Post by Chiuchu on 2008-03-01
Hi, I've the same bug...

This bug is linked to the CDT completion. Try to write the name of a struct followed by a point and you'll get the same. Try also "ctrl+space'...

I don't know how to fix that, but I'm searching. It's really irritating.

bye !

---

