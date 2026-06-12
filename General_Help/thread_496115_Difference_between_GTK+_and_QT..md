---
title: "Difference between GTK+ and QT."
date: 2007-07-08
forum: General Help
---

### Post by gabeyg on 2007-07-08
What is THE Difference between GTK+ and QT?
Thanks.

---

### Post by AlexThomson_NZ on 2007-07-08
GTK (Gimp Tool Kit) is what gnome apps are built on (contains widgets like buttons, labels and dialog boxes, etc.)
QT is the same thing, but for KDE.

---

### Post by az on 2007-07-08
> **gabeyg said:**
> What is THE Difference between GTK+ and QT?
Thanks.

GTK is written in C.  LibQT is written in C++.

QT was around first, but was proprietary (non-free) for a while.  GTK was always free-libre.

GTK is maintained by the community.  QT is pretty much maintained by a company called Trolltech.

---

### Post by gabeyg on 2007-07-08
Thanks!

---

### Post by Jucato on 2007-07-08
Btw, it's Qt, not QT. QT is abbreviation of QuickTime. :)

> **az said:**
> GTK is written in C.  LibQT is written in C++.
QT was around first, but was proprietary (non-free) for a while.  GTK was always free-libre.

That's not 100% true. From the beginning, Qt was originally released under a dual license scheme, a commercial license and a "free" license, the FreeQt License. Unfortunately, it didn't not sit well with both OSI (Open Source Initiative) and FSF (Free Software Foundations), because it prohibited redistribution of modified versions, without Trolltech's approval (but there were modified versions circulating with their approval).

In 1999, with the release of Qt 2.0, the FreeQt license was changed to the Q Public License or QPL. This license was approved by the OSI, but not by FSF, which were the ones making most of the noise (by this time, GNOME 1.0 would be released). And in 2000, Trolltech released Qt 2.2 under GPL, mostly satisfying everyone. And the rest is history.

If we're going to talk about licensing anyway, it's quite ironic that GTK is under the LGPL, which is considered by the FSF, the authors of both GPL and LGPL, to be an inferior, less free, license.

> GTK is maintained by the community.  QT is pretty much maintained by a company called Trolltech.

A bit true, but again, not 100%. Qt has a very active open source community, a large part of which comes from KDE. Trolltech also has in its employ a number of KDE/open source developers, like Matthias Ettrich (founder of KDE) and Zack Rusin. Trolltech also takes in changes coming from the community. Of course, not being tied down to a company has its advantages, but being under an open source license makes the issue a bit inconsequential. KDE, in fact, doesn't use stock Qt coming from Trolltech. The Qt that they distribute contains their patches, which may later be merged with Trolltech's next release of Qt.

GTK+ seems to be more preferred by commercial companies (notably North American ones) because of the licensing. It's also the toolkit of preference by C programmers, although each toolkit have their own binding for other languages.

---

### Post by AlexThomson_NZ on 2007-07-08
It should be clarified that you can use GTK with C++ as well (gtkmm)

---

### Post by Sammi on 2007-07-08
From a users perspective, the only really noticeable difference is the looks. I like both :D

---

### Post by deepclutch on 2007-07-09
C is enough for my li'l brain and gtk+ too ;) (and Gnome)
qt is based on C++ and there seems its proponents saying it is much better because it is on C++ .dont know why it rocks :?(kde?)

---

### Post by az on 2007-07-09
> **Jucato said:**
> That's not 100% true. From the beginning, Qt was originally released under a dual license scheme, a commercial license and a "free" license, the FreeQt License. Unfortunately, it didn't not sit well with both OSI (Open Source Initiative) and FSF (Free Software Foundations), because it prohibited redistribution of modified versions, without Trolltech's approval (but there were modified versions circulating with their approval).

In 1999, with the release of Qt 2.0, the FreeQt license was changed to the Q Public License or QPL. This license was approved by the OSI, but not by FSF, which were the ones making most of the noise (by this time, GNOME 1.0 would be released). And in 2000, Trolltech released Qt 2.2 under GPL, mostly satisfying everyone. And the rest is history..

So what I said was 100 percent true...


> **Jucato said:**
> 
If we're going to talk about licensing anyway, it's quite ironic that GTK is under the LGPL, which is considered by the FSF, the authors of both GPL and LGPL, to be an inferior, less free, license.

What is funny is that free software pragmatists find it hard to reconcile that there is lots of common ground between themselves and free software idealists.  There is no issue here.  Thanks for stirring the pot, though.

(explanation:  Although the lGPL is not ideal, it's a necessary evil, since an extremist position would be worse.  That's why the lGPL exists.  Get over it.)

> **Jucato said:**
> 
...but being under an open source license makes the issue a bit inconsequential. KDE, in fact, doesn't use stock Qt coming from Trolltech. The Qt that they distribute contains their patches, which may later be merged with Trolltech's next release of Qt.


Again, exactly what I said.

> **Jucato said:**
> 
GTK+ seems to be more preferred by commercial companies (notably North American ones) because of the licensing.

To some companies, that's the advantage of dual licencing Qt.  You can make something proprietary out of it, if you pay for that license.

---

### Post by LuisAugusto on 2007-07-10
One is written on C (gtk) the other on C++ (Qt).
Both are open source software.

Qt 4.3 can make things that GTK don't even dream about and it's a lot faster.

---

### Post by Sammi on 2007-07-10
> **LuisAugusto said:**
>  Qt 4.3 can make things that GTK don't even dream about and it's a lot faster.You need some supporting arguments for that empty statement.

---

### Post by AlexThomson_NZ on 2007-07-10
> **Sammi said:**
> You need some supporting arguments for that empty statement.

LOL I agree!  QT causes cancer! gtk is 227% cooler!

---

### Post by LuisAugusto on 2007-07-11
> **Sammi said:**
> You need some supporting arguments for that empty statement.

-Qtopia
-OpenGL engine (3D)
-Canvas 2D engine
-Ability to both render and generate SVG images
-Java Compatibility
-Seamless integration with Microsoft® Visual Studio® .NET (Windows XP/Vista)
-Seamless integration with OS X
 
And there are more!

Ah, BTW, Qt 3 and GTK has more or less the same on speed and consumption, Qt 4.3 it's a notably faster than Qt 3 (around a 20%).

---

