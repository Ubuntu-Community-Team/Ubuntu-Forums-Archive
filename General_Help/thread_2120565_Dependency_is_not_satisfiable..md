---
title: "Dependency is not satisfiable. :\"
date: 2013-02-26
forum: General Help
---

### Post by TripDaRipper on 2013-02-26
I'm trying to install a program called paros
I get this error

Dependency is not satisfiable : libjdic-java

Any help?

---

### Post by matt_symes on 2013-02-26
Hi

What version of Ubuntu are you running ? What release ?

Kind regards

---

### Post by TripDaRipper on 2013-02-26
Ubuntu 12.10 sorry. I'm pretty new to Ubuntu :\ I just switched over from Windows 7 HP 64-bit to this because Ubuntu is clearly better, faster, and more reliable. It's got some pretty nifty tools. The only thing i seem to have trouble with is that it doesn't really allow me to install many things unless these things are in the Ubuntu Software Center. :\

---

### Post by matt_symes on 2013-02-26
Hi

libjdic-java seems to have been discontinued in the repositories. That is why you are seeing this error

> Dependency is not satisfiable : libjdic-java

Source:

[http://lino.ubuntuupdates.org/package/core/natty/universe/base/libjdic-java](http://lino.ubuntuupdates.org/package/core/natty/universe/base/libjdic-java)

How are you trying to install paros ? Where did you get it from ?

Kind regards

---

### Post by TripDaRipper on 2013-02-26
[http://packages.ubuntu.com/lucid/all/paros/download](http://packages.ubuntu.com/lucid/all/paros/download)

That's where i'm getting the packages from. Thanks for helping me, i can't find anything on Google about the issue other than bug reports that aren't helping :\

---

### Post by tgalati4 on 2013-02-26
If it is just one library, you might get away with installing it by finding a debian package for that library from an older Ubuntu distro and using *dpkg -i* to install it.

As long as the library installation does remove conflicting packages, old and new libraries can sit just fine together.  If you have several missing libraries, then it gets tricky--greater chance of breakage.

If the source code is available, you can always build it from source.  That's an exercise at a more advanced linux level.

---

### Post by TripDaRipper on 2013-02-26
I have the source downloaded but idk how to run the build :\

I'm only experienced in PHP, SQL, HTML, C++, Visual Basic, and Java.

---

### Post by matt_symes on 2013-02-26
Hi

libjdic-java also has dependencies as well. I think you may find this difficult to install in 12.10.

```
matthew-S206:/home/matthew/paros % sudo dpkg -i libjdic-java_0.9.5-3ubuntu2_all.deb 
Selecting previously unselected package libjdic-java.
(Reading database ... 348384 files and directories currently installed.)
Unpacking libjdic-java (from libjdic-java_0.9.5-3ubuntu2_all.deb) ...
dpkg: dependency problems prevent configuration of libjdic-java:
 libjdic-java depends on libjdic-bin (>= 0.9.5-3ubuntu2); however:
  Package libjdic-bin is not installed.

dpkg: error processing libjdic-java (--install):
 dependency problems - leaving unconfigured
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Errors were encountered while processing:
 libjdic-java
matthew-S206:/home/matthew/paros % 
```The problem is that you are trying to install a program for Lucid (10.04) and you are using 12.10.

I cannot find it anywhere for 12.10.

[https://launchpad.net/ubuntu/quantal/+source/paros/+builds](https://launchpad.net/ubuntu/quantal/+source/paros/+builds)

Have you considered running a virtual machine with 10.04 and run it in there ?

Kind regards

---

### Post by TripDaRipper on 2013-02-26
No, but i was wondering if there is another proxy program i can use for ubuntu 12.10?

Like WebScarab or Burp Suite but I cant find WebScarab :\

---

### Post by tgalati4 on 2013-02-26
```
apt-cache search proxy
``` brings up a lot of hits.

Try a google search with paros and look for forums where folks are looking for a replacement.  There's probably a good reason it was discontinued--like a better program already exists, or it got morphed into something else.  What is it that you are trying to accomplish?

---

### Post by matt_symes on 2013-02-26
Hi

[http://dawes.za.net/rogan/webscarab/#current](http://dawes.za.net/rogan/webscarab/#current)

Down load the current snapshot jar file. That starts up my on laptop.

Kind regards

---

### Post by TripDaRipper on 2013-02-26
I am trying to get into hacking (Note i am not a black hat hacker nor are my intentions having anything to do with the black hat label or illegal actions) I see a program called XHydra, any info on that? Is that a good replacement? I'm trying to get into hacking because i hear there is big money in that and i am bored of programming. Thanks.

---

### Post by matt_symes on 2013-02-26
Hi

Hacking is not something we discuss on these forums.

If you are interested in Pen testing then there are other distros you can use. 

If i was you, i would take a course on pen testing but these forums are not the place for it.

Thread closed.

Kind regards

---

