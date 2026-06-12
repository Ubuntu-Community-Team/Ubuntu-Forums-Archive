---
title: "samba xp slow, unless VNC is in background"
date: 2006-10-26
forum: General Help
---

### Post by scottpreston on 2006-10-26
this is a tierd thread that there is no solution to (that works for me) but I have found a strange work-around that always works and I am not sure why.

i have a standard xp sp2 box that I am doing an XCOPY to a samba share via a gigabit connection.

it's very slow to samba, about 1/5th the speed as going to another XP box with a 100MB connection.

now i bring up VNC because I am modifiying the smb.conf file and restartig samba, etc. and guess what? VERY VERY FAST, as fast as FTP.

I minimize VNC, VERY SLOW. I bring it back and VERY FAST.

So my guess is there is something happening with the network connection that is causing it go be fast in one case and very slow in another, but I have NO CLUE what it could be.

Thanks,
Scott

p.s. I have tried everything in this forum for a fix but none of them work.

---

### Post by zukakog on 2006-11-12
Bumpity bump.

This is driving my crazy!  What good is a fileserver with gigabit NICs if I only get 200 KB/s.  I get excelent speeds when my other Ubuntu box talkes to my Ubuntu file server, but when My XP SP2 tries to talk to it, it's dirt slow.

---

