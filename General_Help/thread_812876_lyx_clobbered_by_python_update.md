---
title: "lyx clobbered by python update"
date: 2008-05-30
forum: General Help
---

### Post by Sean Patrick Burke on 2008-05-30
Hello fellow kubuntu/lyx users.  Some of you may have noticed that an update this week clobbered the old python library, libpython2.3.so.1.0, a dependency for lyx. 
I have submitted a bug report, but since no one is tracking lyx, it isn't being processed.  ([https://bugs.launchpad.net/ubuntu/+bug/235218](https://bugs.launchpad.net/ubuntu/+bug/235218)).  Has anyone hit this?  Does anyone have a workaround?

Thanks!

Sean

---

### Post by gnomesrule123 on 2008-06-01
i think i may have come across a similar error message now when i try to open any lyx document of export it to pdf it does nothing is this similar to your query??

---

### Post by hazza96 on 2008-06-04
> **Sean Patrick Burke said:**
> Has anyone hit this?  Does anyone have a workaround?
Yes I have hit this, no I don't have a workaround and I really want to be able to write my book on GIMP.

---

### Post by hazza96 on 2008-06-05
I just followed the link to the bug report and mine is not like that.

I can start LyX fine but when I try and open a document it just disappears. When I start LyX using a terminal it says something like 'you found a bug, please report it ...'

It crashes when I try and do what it tells me to.

---

### Post by McAviti on 2008-06-17
My lyx is also broken, i receive the following on the console when starting it:
> QPaintEngine::setSystemClip: Should not be changed while engine is active
QPaintEngine::setSystemClip: Should not be changed while engine is active
QWidgetPrivate::beginSharedPainter: Painter is already active

lyx: SIGSEGV signal caught
Sorry, you have found a bug in LyX. Please read the bug-reporting instructions in Help->Introduction and send us a bug report, if necessary. Thanks !
Bye.
Aborted


I tried to mv the .lyx directory away, but it didn't help. Of course, now i know that the python dependency is ill...

~McA

---

### Post by hazza96 on 2008-06-17
I was having exactly the same problem as you McAviti, I followed the instructions [**here**]("https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/228067/comments/50") and it worked.

---

