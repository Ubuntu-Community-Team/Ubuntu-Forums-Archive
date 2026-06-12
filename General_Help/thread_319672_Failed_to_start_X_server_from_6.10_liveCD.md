---
title: "Failed to start X server from 6.10 liveCD"
date: 2006-12-16
forum: General Help
---

### Post by Fibonacci on 2006-12-16
Hello,

I'm trying to boot Edgy Eft from the liveCD, and I get this error message on a text console:
```
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes>    <No>
```
Okay, [this has happened to me before]("http://ubuntuforums.org/showthread.php?t=254983") - it even complained of not finding a screen (both then and now).
Back then, I solved the problem by starting Ubuntu on "safe graphics mode", so I tried this here but no dice - I still get the same error, and no X server.

I'm still using the nVidia GeForce FX 5200 with which neither Knoppix nor Ubuntu Dapper (in safe graphics mode) have any problems.

Any ideas on how to make it work? Sure, I could download the *other* installation CD, but I have no warranty that it will work if I can't even *start* the liveCD, let alone test it before installing (and I most certainly don't want a system with only a CLI - I'd have downloaded Gentoo if that were the case :P).

Thanks in advance,

-Fibo

---

### Post by firecrotch on 2006-12-16
The Safe graphics mode doesn't work on the Edgy LiveCD.  There's a workaround for it [here]("https://wiki.ubuntu.com/EdgyKnownIssues/59618")

---

### Post by Fibonacci on 2006-12-16
> **firecrotch said:**
> The Safe graphics mode doesn't work on the Edgy LiveCD.  There's a workaround for it [here]("https://wiki.ubuntu.com/EdgyKnownIssues/59618")

Thank you! I'm posting this from Edgy right now.

---

### Post by fsando on 2006-12-16
I am having the same problem on an ASUS W1Jc (ati mobility x1600, 1680x1050).
The livecd either stops halfways through or gets all the way through but ends up with a garbled (and useless) screen
Is there any chance a new livecd will be created that works with x1600 / 1680x1050?

---

