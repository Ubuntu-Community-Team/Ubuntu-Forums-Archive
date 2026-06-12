---
title: "2 GB RAM Boots Normal any more, not so much"
date: 2007-11-16
forum: General Help
---

### Post by boscorillium on 2007-11-16
So I'm running a intel core 2 duo, asus motherboard and other good stuff (I can provide details if necessary). The important details, as I see it are that it's gutsy gibbon, 64 bit and with 2 GB or ram it boots fine and runs GREAT. When I put an additional 2 GB in (or just 1 more for that matter) all matched 1 GB sticks (ddr2-800) it basically stops working. Everything takes forever, the boot process is multiple minutes.

Like it's been twenty minutes and it's just now getting to the login screen, but it's still showing the "waiting" icon and there is nothing on the screen except the light brown background.

If I remove 2 GB, runs fine. Doesn't matter which sticks or which slots. To boot (pun intended) Windows works FINE. I think that part frustrates me the most. :)

Any help would be GREATLY appreciated. Is there something I can do when it runs fine to give information about why it is sucking so bad with 4 GB? Because the system is basically unusable with 4GB in it.


Thanks,


Tim

---

### Post by pjkoczan on 2007-11-16
> **boscorillium said:**
> So I'm running a intel core 2 duo, asus motherboard and other good stuff (I can provide details if necessary). The important details, as I see it are that it's gutsy gibbon, 64 bit and with 2 GB or ram it boots fine and runs GREAT. When I put an additional 2 GB in (or just 1 more for that matter) all matched 1 GB sticks (ddr2-800) it basically stops working. Everything takes forever, the boot process is multiple minutes.

Like it's been twenty minutes and it's just now getting to the login screen, but it's still showing the "waiting" icon and there is nothing on the screen except the light brown background.

If I remove 2 GB, runs fine. Doesn't matter which sticks or which slots. To boot (pun intended) Windows works FINE. I think that part frustrates me the most. :)

Any help would be GREATLY appreciated. Is there something I can do when it runs fine to give information about why it is sucking so bad with 4 GB? Because the system is basically unusable with 4GB in it.


I've seen issues like this before at work, namely having to muck with either BIOS settings on your motherboard or tweaking a kernel parameter somehow, but only with 32-bit versions of the os (usually running a dedicated huge-memory model kernel works, but 64-bit is essentially a huge-memory kernel). The first thing you can do is determine if this is a hardware problem.

Try running memtests (hey, it's included in the livecd, how convenient), as one of the sticks or slots could be bad. Also, try different combinations and ordering of the memory sticks to see if problems follow sticks or slots.

If that doesn't work, post more specific info of your board and one of the forumites, possibly me, will be able to help you further.

---

### Post by pjkoczan on 2007-11-16
Also, if you can handle the slowness of booting up/logging in, you should paste the output of the command "cat /proc/meminfo" when all 4 GB are in. That will determine if the OS can't see it for some reason.

---

### Post by bingoUV on 2007-11-16
Which Asus motherboard do you have? I also have a similar problem. For 64 bit OS to recognize more than 2.8 GB of RAM, they asked me to enable some "memory remap" feature in BIOS. But when it is enabled, everything happens in slow motion. 

It has nothing to do with ubuntu, or even linux. Same thing happens in solaris and windows XP too. It has to do with stupidity of Asus.

Is this similar to your story?

---

### Post by boscorillium on 2007-11-16
Well I'm not sure my system will ever be usable after login. I tried late last night and couldn't get anywhere near functional. I couldn't even run a command (alt-f2). 

I do have an ASUS motherboard. It's a p5n32-sli (i think is the model). 

But I think some critical details are being glossed over. One is that Windows boots and runs FINE. Not a hitch.

Also, I didn't mention that with Feisty, this problem didn't exist. I was definitely running Feisty with 4 GB no problem. It may have slightly underreported the amount I had by .4 or so GBs, but that was tolerable. I do a lot of virtual machine work and as such need all the ram I can get.

Thanks for the replies. Anyone else?

---

### Post by boscorillium on 2007-11-17
bingoUV you are my hero. It sucks that this doesn't work for me, but enabling memory remapping did the trick for me. Ubuntu is back to its good old self. I am so happy you mentioned that.

Thanks again!

---

