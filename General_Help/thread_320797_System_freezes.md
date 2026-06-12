---
title: "System freezes"
date: 2006-12-17
forum: General Help
---

### Post by erythro on 2006-12-17
Hi,

My Ubuntu 6.10 has been freezing on me seemingly at random. Everything locks up and becomes completely unresponsive, including the keyboard. Although, if any sound was playing during the freeze, it would go on playing normally.

I can't detect a pattern to this so it's hard to pinpoint the cause. Is there some sort of log file I can check or something that would help me figure this out? I searched the forums but couldn't find anything on random lockups.

I love Ubuntu. Need to fix this little quirk and I'll love it even more. ](*,)
Any ideas?

---

### Post by riven0 on 2006-12-17
Can you tell us the specs of your machine and what program(s) you are running when the comp locks ups?

---

### Post by erythro on 2006-12-18
Pentium 4 3.0GHz with HT
Nvidia 6600GT

Here's what's running when it locks up, but since it happens randomly, I'm left guessing.

Always running:

beryl, beryl-manager
kiba-dock

Usually running:

Thunderbird
Firefox
Gaim

Sometimes running:

Amarok
vlc


I doubt any of this helps. Isn't there some log file that reports system errors or driver errors or something?

---

### Post by wpshooter on 2006-12-18
My **guess** is that it is related to the beryl program you are running.

I have seen post on here similar to yours and invaribly the poster was running the beryl program, whatever it is !!!

---

### Post by endersshadow on 2006-12-19
Probably not.  Mine is randomly crashing, as well, and I disabled beryl AND AIGLX, with still the same result.  I've changed sound settings, but to no avail.  I'm still trying to figure this out...

---

### Post by erythro on 2006-12-20
Today went by crash-free. I hope it stays this way. I still don't know what was/is causing it. I'll post updates if anything develops. And good luck with yours, endersshadow.

---

### Post by holdinout on 2006-12-20
I'm not running the beryl program, and I've had a similar crash.
Everythings nonresponsive, mouse moves, and requires a restart.

---

### Post by endersshadow on 2006-12-20
Hopefully this won't jinx it, but I've read that there seems to be a problem w/ powernowd.  I just did a sudo apt-get install cpufreqd, and let it take care of itself.  I'm really hoping this solves it, but I'll keep you updated!

---

### Post by ddumanis on 2006-12-20
In my experience, random freezes are caused by hardware problems. A memory module that has gone bad after years of use... a CD-ROM drive in a laptop with a loose connection... etc., etc.

Have your hardware checked out.

---

### Post by erythro on 2007-04-14
It's been a while, but I finally figured out what the problem was. My GPU was overheating because the fan was slowly dying, causing complete lockups. The fan finally gave out completely recently which is how I finally realized what was going on. So, ddumanis, you were right on the money.

---

### Post by octopussz on 2007-04-24
Finally I  I didn't suffer from system freeze now!! 
I am using Thinkpad T43 with ati X300 card
For me the problem seemed to be the default ati driver installed doesn't work well with the beryl coming with feisty

For it's a bit too long to post in a reply please refer to my msn space for details
[http://octopussz.spaces.live.com/blog/cns!F5DBD1F61123DAB1!4262.entry](http://octopussz.spaces.live.com/blog/cns!F5DBD1F61123DAB1!4262.entry)

Hope it will work for you guys!
If it can't please also let me know~

---

