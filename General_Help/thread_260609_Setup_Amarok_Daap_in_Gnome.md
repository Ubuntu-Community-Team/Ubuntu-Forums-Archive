---
title: "Setup Amarok Daap in Gnome"
date: 2006-09-19
forum: General Help
---

### Post by spockrock on 2006-09-19
is there a way to setup and configure zeroconf in gnome for those who dont use kde but want to take advantage of the new daap feature in amarok?

---

### Post by orb9220 on 2006-09-19
Sorry I think you are out of luck.

Amarok relies heavily on the kde-libraries and dcop so kde-core is required.

---

### Post by spockrock on 2006-09-19
:( man too bad amarok is sooo amazing, I havent found a good gnome counterpart.  Nothing handles my music collection as good as amarok, everything else pretty much just dies, and become useable.

---

### Post by ronjouch on 2008-06-11
> **orb9220 said:**
> Sorry I think you are out of luck.

Amarok relies heavily on the kde-libraries and dcop so kde-core is required.
Hello,

Quite old topic, but I the same problem as spockrock: I'm using Ubuntu, love Gnome + Amarok and can't get daap to work.

I have lots of disk space and don't care about installing extra kde libs. Could somebody tell me what I need to install? The metapackage kde-core will be okay? Or maybe I can restrict a bit? (I said I have disk space, but of course if somebody can specify me a more restrictive set, I'll go for it)

Thanks for your help!

---

### Post by bismark on 2008-07-22
> **ronjouch said:**
> Hello,

I have lots of disk space and don't care about installing extra kde libs. Could somebody tell me what I need to install? The metapackage kde-core will be okay? Or maybe I can restrict a bit? (I said I have disk space, but of course if somebody can specify me a more restrictive set, I'll go for it)

Thanks for your help!

Try installing the avahi libraries for qt.  I needed to install libavahi-qt4-1.

---

### Post by ronjouch on 2008-07-23
Hello, 

Seems strange to me to install the qt4 version for my amarok-qt3, but I'll try it.

Thanks!

---

