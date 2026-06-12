---
title: "Gambas / Visual Basic Program"
date: 2008-04-21
forum: General Help
---

### Post by Venko on 2008-04-21
Hey,

I'm after a program that I can use along the lines of Visual Basic for Ubuntu. I took a quick look at Gambas however this is not an option as it is developed for Qt, not GTK+.

My past experience with running Qt programs and libraries inside GNOME tells me to stay the hell away from them as they will not be stable and will result in Qt libraries using up my resources constantly for the one Qt program that I might use on occasion.

I don't want / have the ability to learn C/C++/C#/etc to develop applications. I have looked at Python and there's nothing along the lines of a "Visual Python" >.<

Any help will be much appreciated.

---

### Post by heartburnkid on 2008-04-21
MonoDevelop will let you program in VB.NET on Linux.

---

### Post by Venko on 2008-04-21
Perhaps you misunderstood. I'm after something along the lines of Visual Basic (the program). It doesn't have to be a BASIC language so long as it's simple enough to learn and has a similar IDE.

MonoDevelop doesn't seem to provide anything like Visual Basic in terms of interface.

---

### Post by kalaharix on 2008-04-25
The latest versions of Gambas can use either GTK+ or Qt.

Install Gambas2 from Synaptic and then add the following to system, admin, software source, third party software: 
deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) hardy main
(substitute gutsy for hardy if still on Ubuntu 7.1)

In time, this will upgrade from 2.0 to 2.5.

Gambas2 is underrated and ideal (in my case) for simple database frontends. It is stable if a little incomplete and the documentation is not great (no criticism: only so many hours in the day etc etc). It is not a clone of VB but similar enough to be understandable to VB programmers. The documentation does not make it ideal for new programmers.

Don't believe the rantings of the Python brigade: the TIOBE index still lists (Visual)Basic in third place behind Java and C.

---

### Post by Venko on 2008-04-25
kalaharix, you are right that Gambas can produce GTK+ projects.
However the development IDE still requires Qt libraries (which aren't
welcome in a happy experience in Gnome installation).

Basically, KDE users can happily develop for GNOME and KDE but GNOME and XFCE users aren't allowed to get in on the fun.

---

### Post by Venko on 2008-04-25
**Edit:** Sorry, seems the server's current instability caused my browser to submit the post twice.

---

### Post by kalaharix on 2008-04-26
That's interesting. Just as a matter of interest, if a Gambas GTK program is compiled, taken to another machine and run with Gambas runtime: would it be Qt-free?

Have you looked at REALbasic? It is (currently?) free in std form (1 user integrated SQLite) although the Pro version is 'traditionally' (i.e. ridiculously) priced. If you are a corporate user this would not be a major problem. The documentation is very good and wistfully makes me wonder about the 'free' software model.

---

### Post by Venko on 2008-04-26
I think it would be but I can't say for sure. From what I read on their mailing list it is only the editor (the actual program that makes the programs) which is only available in Qt.

As for using REALbasic I think that's going a step too far in the direction of proprietary software. Flash-nonfree is bad enough but using a proprietary program for my application development?

---

### Post by kalaharix on 2008-04-28
I have to say that I have had nothing but joy from Gambas2. Install from Synaptic rather than Ubuntu package manager. Click on Gambas2 and it will check everything except one line which should be manually checked. Add the following to system, admin, software source, third party software:
deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) hardy main
(substitute gutsy for hardy if still on Ubuntu 7.1)

In time, this will upgrade from 2.0 to 2.5.

The documentation is not great, many of the examples have problems, most of the GambasForge examples have problems but the core product is great particularly if you come from a VB background.

It is only Linux. If you need cross-platform then PureBasic and REALbasic are two commercial options.

---

