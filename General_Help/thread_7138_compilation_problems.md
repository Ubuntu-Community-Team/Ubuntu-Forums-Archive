---
title: "compilation problems"
date: 2004-12-04
forum: General Help
---

### Post by Magneto on 2004-12-04
OK running warty on a p3 450mhz 512mb ram system -
For some reason when trying to compile a new kernel the make process would fail constantly although I can keep restarting it and it will eventually finish.  I had to upgrade gcc to 3.4 and compile it in single user mode because the screensaver would kill the make process and another time just trying to do it from gnome-term eventually froze the whole system.

compiling it in single user mode had it finished quick and without errors- so is Ubuntu hostile to this older hardware or what?

---

### Post by TravisNewman on 2004-12-04
I had a similar issue with Warty on more modern hardware (Athlon XP 1800+, 512 megs, It hink the board was made in 2002). The screensaver wouldn't kill the process, but I WOULD keep getting errors and crap like that. Then frequently it wouldn't work after boot until I recompiled it.

Memtest says my ram is fine.

---

### Post by Magneto on 2004-12-04
the screensaver won't kill it everytime but id always get make errors at some point
memtest i ran before because I had issues with this box on many systems- memtest showed nothing so I ran ubuntu install thet other day when setting it up and segfaults when trying to install the base! so I started testing the memory I had based on the segfaults lol it worked found two bad pieces of ram and now im good to go cept for that other thing - but no probs now with my new kernel - none so far at least

ive had this issue in slackware 10's installation process and OS, fedora core 2 and 3 - i couldnt compile drivers or kernels in fedora and it sucked

---

### Post by jdong on 2004-12-04
What kind of 'errors' are we talking about?


Have you done a memtest?

---

### Post by jdong on 2004-12-04
and I wouldn't say Ubuntu is harsh on old hardware -- I'm running it on a 486/75MHz!!

---

### Post by TravisNewman on 2004-12-04
[QUOTE=jdong]and I wouldn't say Ubuntu is harsh on old hardware -- I'm running it on a 486/75MHz!![/QUOTE]

Ech... why would you want to? *LOL*

I don't remember the specific errors unfortunately.

And Magneto, when you say it found the "bad pieces of ram" do you mean bad sticks or bad individual parts, because if it's individual parts and you can disable that, I have another 512 I can throw in ;) I've always wondered if it was possible to just disable the bad sectors, but never followed up on researching it.

---

### Post by jdong on 2004-12-04
that's besides the point...


Speaking of bad RAM, I just discovered that my two-week-old laptop has a stick of bad RAM (that I bought on black friday... my luck)... Took me a while of denial to figure this one out... Surprisingly, only Windows had weird issues with it.


Time to use that good old exchange policy!

---

### Post by Magneto on 2004-12-04
jdong- i ran memtest before I even installed Ubuntu, there is nothing wrong with the hardware -the errors were all error 2 from make with no info and if i ran make again it would compile the kernel piece that it faulted on previously and proceed until another error- 
 i have no more errors after upgrading to gcc 3.4 and now with my new kernel everything seems better - had gnome-terminal crap out once but thats about it
Bestbuy got ya huh -better than compusa those bastards suck


panicked--since memtest couldn't find any problems and I was segfaulting through every OS install process I tested the memory sticks individually by running ubuntu's install and if it ran without segfaulting I knew it was good -using that method I found two 128mb sticks that had issues- memtest couldnt find any issue but the other way did weird- especially with that long ass memtest , waste of time

---

