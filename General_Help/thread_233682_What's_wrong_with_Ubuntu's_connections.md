---
title: "What's wrong with Ubuntu's connections??"
date: 2006-08-10
forum: General Help
---

### Post by AlliumPorrum on 2006-08-10
Hi!

Previously I asked here what's wrong with the WinSCP, because it's crashing the whole Ubuntu server. But now I've noticed that it has nothing to do with WinSCP; no matter if I use WinSCP, Winzilla, MySQL admin tools,  
or basically any app that creates a socket connection from my Windows client to the Ubuntu server, the Ubuntu server keeps crashing all over again. It just halts, and only way to get it up and running is hardware reboot. 

Does anyone have any ideas what's wrong and how to fix it? 

Few friends of mine already told me that for server environment some other distribution might be more stabile that Ubuntu, but I wouldn't want to install everything all over again... Please help me:confused:

---

### Post by snellgrove on 2006-08-10
I dont know how to fix this,

but I suspect the best thing to do is to check the /var/log folder, and see if theres anything in there that might help.

Any idea when these crashes started happening?

sounds quite major if its causing the whole thing to lock, you may end up uninstall / installing again anyway if your not lucky.

---

### Post by AlliumPorrum on 2006-08-10
Yeah well, there's about 100 files in that /var/lib/ directory, so what should I look for??

These problems started right away after I installed Ubuntu;=) I mean, it has been crashing all the time when some socket connection has been created from other computer.

I really wouldn't want to install all over again, but certainly, if I really-really have to, I think I'll try Debian or something like that for next.

---

### Post by AlliumPorrum on 2006-08-12
Doesn't anyone have really have no idea how to fix this problem?? I'm starting to be quite desperate, so all hints and suggestions are more than appreciated...

---

### Post by AlliumPorrum on 2006-08-13
Me again, sounding desperate...;=)

If no one can tell me how to fix this problem, could someone please give me a hint for finding the reason for the problem?? Is there some logs or debugging applications that I could use for solving the problem??

I just realized that I cannot install new Linux version before I get a backup of my MySQL DB, and currently I cannot do it because all applications that I have tried crash. Darn.

---

### Post by AlliumPorrum on 2006-08-15
Ok, I fixed the problem. I was using 686 kernel (on my Pentium 3 laptop), but now when I changed back to the original 386 kernel, everything seems to be working just fine!

---

