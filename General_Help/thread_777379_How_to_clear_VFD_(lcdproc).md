---
title: "How to clear VFD (lcdproc)?"
date: 2008-05-01
forum: General Help
---

### Post by hihp on 2008-05-01
Hi,

I am running a Mythbuntu 7.10 on a machine in an Antec Fusion 430 case with an iMon-compatible VFD (maybe it actually is an iMon, I am not sure, but the drivers for it definitely work).

After a lot of fiddling around, it was pretty easy to get the display to work, and working it is indeed fine, so this is not a question on how to get MythTV use the display or anything.

The problem is this: if the system is shut down, the display retains the last content it was shown before lcdproc is stopped, which is (and strangely enough I cannot find where this is ever set) a goodbye message which I cannot find anywhere; in the file /etc/LCDd.conf, I already set 
```
GoodBye=' '
```
(I also tried the empty string ''), but that seems to be ignored.

So what I want to achieve on shutdown of the system is this:
the VFD should be cleared and show nothing.

Can somebody give me a push in the rioght direction?

---

