---
title: "Rename of the root group"
date: 2007-06-07
forum: General Help
---

### Post by chelala on 2007-06-07
Hi

I installed xubuntu to a friend not very experienced in linux, sudos, .... (I'm NOT experienced).

He wanted to create (add) a user, gksudo asked for password confirmation, he entered it, and (donk know how) what he did was rename the group "root", finnaly. when restarted all the other groups disappeard, and his user no longer could do sudo (as admin group disapeared aswell). My solution was enter in recovery mode, change back root group anem using groupmod, and ALL the others, video, scanner, floppy, adm, cdrom.... and many others group with groupadd, then it all worked.

My question: Besides the loss of all the groups there any other problem, because of the root group rename? should I do something else ?

my opinion is xubuntu (and other ubuntus is they allow it) should no allow the change those critical groups in the graphical environment

thanks in advance

Harold Chelala

---

### Post by kidders on 2007-06-08
Hi there,

Although I can't say I would ever recommend doing it, *renaming* a group shouldn't make any difference at all, since its the GIDs (ie not the names) that are important. Perhaps your friend did something else?

> **chelala said:**
> my opinion is xubuntu (and other ubuntus is they allow it) should no allow the change those critical groups in the graphical environmentIt's impossible to do such a thing as an unprivileged user. Once you become root though, Linux always assumes you know what you're doing, so there are no safety nets. (Any other policy would probably just be irritating for advanced users!)

Unless you know exactly what you're doing (ie you know Linux's user management system inside out), and manage to track down what your friend did that made everything go weird, I would strongly recommend reinstalling. There's any number of places a major security hole (or other problem) may have crept into his system ... and that's something a beginner can do without!

[SIZE="1"][COLOR="Silver"][UAResolved][/COLOR][/SIZE]

---

