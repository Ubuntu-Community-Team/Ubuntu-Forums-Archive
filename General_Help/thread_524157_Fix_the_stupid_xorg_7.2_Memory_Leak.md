---
title: "Fix the stupid xorg 7.2 Memory Leak"
date: 2007-08-12
forum: General Help
---

### Post by walmartshopper67 on 2007-08-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've seen many posts, many threads, many bug reports ([https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882)) about the cursed memory leak in xorg 7.2 - I have been dealing with this for months, and it is getting flat out ridiculous - restarting my computer 3 times a day because of xorg, and a lot of people are having the exact same problem, but there is no way to fix it. Well, theres a patch, but I have no idea what you're supposed to do with it. There is supposedly a patch, mentioned here on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882) but, apparently nobody knows where it is judging by this: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882/comments/6](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/92882/comments/6)

One last time - does anyone know where the patch/fix is? Anyone, anywhere? Because this is crap.


I realize this is open source, but I'm not trying to do anything complicated here - just go more than 6 hours without having to reboot the wretched thing, or is Ubuntu really this big of a cluster*#!% that I can't even do that. (and I'm saying that as a loyal Ubuntu user - until Feisty everything has been fine, hell i didnt have the problem in the Feisty herds - but now after its release i've been wrestling with the piece of crap just trying to keep it from using all my memory)

---

### Post by pointone on 2007-08-13
[https://launchpad.net/ubuntu/+source/xorg/+bug/77606](https://launchpad.net/ubuntu/+source/xorg/+bug/77606)

Or better yet:

[http://launchpadlibrarian.net/6845379/1.2.0-client-leak.patch](http://launchpadlibrarian.net/6845379/1.2.0-client-leak.patch)

---

### Post by walmartshopper67 on 2007-08-15
Yeah - I just found out that xorg is patched in Ubuntu for bug 92882. Apparently i've discovered another xorg bug/memory leak with the same symptoms. 

Great. Now I have no idea what the hell to do. Just sit here with a half-assed Ubuntu install.

---

