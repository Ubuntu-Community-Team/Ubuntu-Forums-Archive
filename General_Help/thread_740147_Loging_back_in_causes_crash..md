---
title: "Loging back in causes crash."
date: 2008-03-30
forum: General Help
---

### Post by CLomax on 2008-03-30
This may be a problem which is easily solvable/already solved, but I couldn't find any other threads on it, Google didn't give results either. So, this is really two problems rolled into one; first problem is that most times when I log out, I try to log back in only for it to freeze which causes me to do a hard shutdown because I don't know any better. It gets to the point where I hear the welcoming sound and it freezes just as it starts loading compiz, judging by the cross-like icon as the cursor. The same sort of thing happens if I try to change the resolution of a program, for example, a game. It logs me out, and if I try logging in, same thing happens.

I have a feeling that it may be because I downloaded the wrong Ubuntu image; without much thought I downloaded the one that is for 64bit AMD and Intel computers but mine has x86 architecture. I have a feeling that this may be causing a few other bugs I have since my brother's Ubuntu installation runs well with no noticeable bugs.

If you can help or need more details, please advise.

---

### Post by dmitriyp13 on 2008-03-31
There should be a clue to the X crash in one of the log files in the /var/log folder.  The best ones to start would be 'messages' and 'syslog' but there might be useful info in other ones.

> **CLomax said:**
> I have a feeling that it may be because I downloaded the wrong Ubuntu image
As far as I know, you cannot install a x64 architecture on an i386 machine.  You will get an error during the install.

---

