---
title: "apt architecture parameter (if there is one)"
date: 2012-12-01
forum: General Help
---

### Post by Schotty on 2012-12-01
Greetings.

As a long time Red Hatter I am lacking the understanding of alot of some of the nuances and inner workings of dpkg and apt.  

I have a problem that I could easily solve with yum/rpm and presume there is a solution on dpkg/apt -- forcing the architecture to 32bit from 64bit.  

IE:

sudo yum install foo.i386 bar.i386 nachos.i386 beer.i386


I am sure there is a way to do this on dpkg/apt, but how?  I have a few packages that I need the i386 versions of that the compat package isn't doing the trick.  Rather than go ape as instructed and manually dropping files from the 32 bit revision, I am going to use the package manager for what it was invented for :P

TIA,
Andrew

---

### Post by Cheesemill on 2012-12-01
How about trying:
```
sudo apt-get install foo:i386 bar:i386 nachos:i386 beer:i386
```

---

### Post by Schotty on 2012-12-02
That was it, thanks!

---

