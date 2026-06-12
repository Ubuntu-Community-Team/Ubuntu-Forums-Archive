---
title: "internet 'freezes' in gutsy"
date: 2007-11-09
forum: General Help
---

### Post by Angelbeast on 2007-11-09
I've been having this problem since upgrading to Gutsy. sometime, say every day or two, my internet connection will just freeze and i have to restart to get it to work again. It' not a router issue since it did it on the old router and a new one. everything else will work fine like the mouse and the keyboard and sound...Just no internet and it does show that i am connected and that there is traffic. Is anyone else having this problem?

---

### Post by troyer81 on 2007-11-09
I don't know if it's your issue, but I had numerous issues with slow, if not completely halted, internet usability because of the IPv6 protocol being on by default.  For the most part, you should be safe disabling IPv6 since no one uses it yet (in general).  Here's a link to one (of many) articles that discuss this issue.

[http://ubuntuforums.org/showthread.php?t=589011](http://ubuntuforums.org/showthread.php?t=589011)

I think the easiest way of disabling it is through blacklisting the IPv6 module (described in the article above), but there are many options.

For the most part, people seem to experience "slow" internet, rather than "no" internet, but I sometimes had to completely restart to get it working again.  At any rate, I would give it a try if I were you :-)

Good Luck!

---

### Post by Angelbeast on 2007-11-10
> **troyer81 said:**
> I don't know if it's your issue, but I had numerous issues with slow, if not completely halted, internet usability because of the IPv6 protocol being on by default.  For the most part, you should be safe disabling IPv6 since no one uses it yet (in general).  Here's a link to one (of many) articles that discuss this issue.

[http://ubuntuforums.org/showthread.php?t=589011](http://ubuntuforums.org/showthread.php?t=589011)

I think the easiest way of disabling it is through blacklisting the IPv6 module (described in the article above), but there are many options.

For the most part, people seem to experience "slow" internet, rather than "no" internet, but I sometimes had to completely restart to get it working again.  At any rate, I would give it a try if I were you :-)

Good Luck!

I think the culprit MAY have been a Pidgin plugin..It seems to be fine as of right now...but if it does it again i will try what you suggested...Thanks for all of your help :-)

---

### Post by Angelbeast on 2007-11-11
> **troyer81 said:**
> I don't know if it's your issue, but I had numerous issues with slow, if not completely halted, internet usability because of the IPv6 protocol being on by default.  For the most part, you should be safe disabling IPv6 since no one uses it yet (in general).  Here's a link to one (of many) articles that discuss this issue.

[http://ubuntuforums.org/showthread.php?t=589011](http://ubuntuforums.org/showthread.php?t=589011)

I think the easiest way of disabling it is through blacklisting the IPv6 module (described in the article above), but there are many options.

For the most part, people seem to experience "slow" internet, rather than "no" internet, but I sometimes had to completely restart to get it working again.  At any rate, I would give it a try if I were you :-)

Good Luck!

Okay i had it happen again so i tried the instructions in the thread...Hopefully that will work :-)

---

### Post by Angelbeast on 2007-11-14
Well...After following the instructions in the above posted thread it SEEMED like it had worked between the even more excessive hard lockups that i have been having a proble with since feisty...I just had the internet freeze up again...any other suggestions? *LOL*

---

### Post by Angelbeast on 2007-11-14
Hmmm...two more internet freeze ups in ten minutes and yet another hard crash...

now where did i put that windows disk? haha

---

### Post by Angelbeast on 2007-11-15
Had 2 more so far today...i am SO sick of this between this and locking up i spend more time rebooting than anything else...does ANYONE have anymore ideas? could it be something with ndiswrapper?

---

### Post by mike555 on 2007-11-15
You might try a different browser , if that other one works then maybe you should uninstall Firefox , delete your Firefox profile in your home folder (hidden) then reinstall ........

---

### Post by Angelbeast on 2007-11-15
> **mike555 said:**
> You might try a different browser , if that other one works then maybe you should uninstall Firefox , delete your Firefox profile in your home folder (hidden) then reinstall ........

hey mike...i actually have done that...i went back to swiftweasel and deleted all firefox stuff and started over with swiftweasel from scratch...i don't know if it's a browser issue though since i lose my connection completely...in my messenger and if i'm streaming some music...email...nothing will work...i'm thining about trying to new driver for broadcom in the restricted driver manager...

now if i were to do that i remember to get the ndiswrapper to work i had to blacklist something...would i have to undo that? and if so how do you unblack list something?  *LOL*

---

### Post by Angelbeast on 2007-11-18
so i am STILL the only one in the world whose internet traffic freezes in Gutsy? WTF?

---

### Post by Angelbeast on 2007-11-18
COULD it e something wrong with ndiswrapper??

---

### Post by wsscott on 2007-11-18
Not sure if this is a related problem, but I have completely lost firefox.  It simply will not load. I have removed it and reinstalled with no luck.  I removed Pidgin after reviewing this thread, but that didn't help either.  I believe firefox worked fine until I applied some of the recent patches.

---

### Post by Angelbeast on 2007-11-18
> **wsscott said:**
> Not sure if this is a related problem, but I have completely lost firefox.  It simply will not load. I have removed it and reinstalled with no luck.  I removed Pidgin after reviewing this thread, but that didn't help either.  I believe firefox worked fine until I applied some of the recent patches.

Have you tried using Swiftweasel?

---

### Post by Angelbeast on 2007-11-20
Okay well i did figure out that i had the driver from my 32 bit windows disk so i removed that and installed a 64 bit driver and that MAY have curd my hard crashes and i thought it may have cured this issue as well but i just had another traffic freeze today...it HAS been over 2 days though...anymore ideas?

---

### Post by jimbojones on 2007-11-21
I am running Gurtsy, IPW3945 wireless or a Novatel air card....anytime I have alot of bandwidth hungry processes my Laptop freezes completely and I have to hld the power button to restart.  Ha shappened since day one so you are not alone.  No problems in Feisty

---

### Post by Angelbeast on 2007-11-21
> **jimbojones said:**
> I am running Gurtsy, IPW3945 wireless or a Novatel air card....anytime I have alot of bandwidth hungry processes my Laptop freezes completely and I have to hld the power button to restart.  Ha shappened since day one so you are not alone.  No problems in Feisty

well at least now i know i'm not alone :-)

---

### Post by knotty on 2008-01-16
My internet also freezes at times in Ubuntu. I followed a suggestion to uninstall and completely remove firefox and when I installed it again, I was able to browse the net again. But this problem returned and when I uninstalled and installed it once more there was no difference. So I just hot lucky before. My machine is a Dell 1300. This is a pain. I can still use my torrent client and stream music, but cannot download updates or browse the net. The IPv6 is set to false in About:config, so I guess that it is off.

---

