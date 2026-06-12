---
title: "ISDN driver causing trouble with hibernate?"
date: 2006-12-16
forum: General Help
---

### Post by juraj on 2006-12-16
Ok, a long time ago, while I was still using dapper, I noticed my box wouldn't hibernate. I've tried everything at that time - hibernate2, and stuff, but with no success.

I'm now a happy edgy user ;) and have got a hitch to resurrect the damn hibernation. It can't be that ubuntu's hibernation features suck so much. It would always just return to a locked session.

Ok. Recently while I was using the tty consoles I noticed this message:
[17179585.036000] mISDN: INTERNAL ERROR in drivers/isdn/misdn/stack.c:596

After further inspection, I figured out that specific message is always there if I grep the contents of dmesg with "misdnd", on every boot. I have an Asuslink ISDN card in my box but I have never used it - I may, eventually, if my DSL connection breaks or something. Anyway, I have noticed that a failure related to mISDNd appears when I attempt to hibernate:

[17181083.728000] Stopping tasks: 
=====================================================
[17181105.060000]  stopping tasks timed out after 20 seconds (1 tasks remaining):
[17181105.060000]   mISDNd
[17181105.060000] Restarting tasks...<6> Strange, mISDNd not stopped

So, not only this module uselessly sits in memory as I don't use it, it causes trouble, too!

I rmmod them all:

juraj@brot2ubuntu:~$ sudo rmmod mISDN_l1
juraj@brot2ubuntu:~$ sudo rmmod mISDN_l2
juraj@brot2ubuntu:~$ sudo rmmod mISDN_core 
(I have to rmmod an additional module, don't correctly know it's name, I know it begins with w996 or something, because it depends on mISDN_core)

Surprise, surprise! My system finally successfully hibernates for the first time! Although I see two weird messages saying something about changing the power state and failure to open something, it successfully hibernates, and successfully resumes!

Now, what should I do? File a bug on this module? Blacklist it? Somebody help me.

BTW, this occurs on a fresh install of edgy, so third party stuff is excluded.

---

