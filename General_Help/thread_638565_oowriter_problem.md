---
title: "oowriter problem"
date: 2007-12-12
forum: General Help
---

### Post by iraiscoming223 on 2007-12-12
Hello everybody!
I have a (hopefully) tiny problem here.
Every time I try to run oowriter (the other programs from the suite work great!) it shows up and then crash immediatly with this output:
```
X-Error: BadAlloc (insufficient resources for operation)
        Major opcode: 53 (X_CreatePixmap)
        Resource ID:  0x3400246
        Serial No:    3152 (3152)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging


```
I've googled around a lot, played also with .Xauth.conf, .gtkr and so on, but nothing changed.
I can't get rid of this problem. I'm using abiword right now, but I don't "fell @ ~", if you know what I mean... :)

If it could be useful, oowriter ran with another user works perfectly...

Any idea?

I already tried:
- (delete .Xauth.conf) sudo dpkg-reconfigure xauth
- sudo apt-get remove openoffice --purge, sudo apt-get install openoffice
- removing .openofice2 configurations folder in my home dir
- many other stuff -.-

Thanks in advance! :)
Greetings from Italy!

**P.S.** I guess it must be something with some stuff or config file in my ~/ because I've recently made a clean install of Gutsy, but the problem persists (my home dir is on another partition)

---

### Post by iraiscoming223 on 2007-12-13
\\:d/
Up
\\:d/

---

### Post by mcduck on 2007-12-13
I've found the same problem when using some theme engines (DynDyn actually). Go to System/Preferences/Appearance and use some other controls theme.

---

### Post by iraiscoming223 on 2007-12-13
> **mcduck said:**
> I've found the same problem when using some theme engines (DynDyn actually). Go to System/Preferences/Appearance and use some other controls theme.

WTF!! (sorry ¬¬) You're right, you saved me man!!! Thanks!!
Tell me when you come to Italy, I'm gonna offer you a beer!!
Anyway, this is awful ¬¬

---

