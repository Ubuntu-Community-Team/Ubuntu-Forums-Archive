---
title: "Login issues on Feisty server (prompt displayed too soon?)"
date: 2007-04-28
forum: General Help
---

### Post by pewtermoose on 2007-04-28
I recently installed Feisty server and I'm loving it except for an issue I'm having after the first login.  It installs fine and boots up and I log in.  I've done nothing else except for and apt-get update/upgrade and install ssh.  After that I happened to reboot and this is where I'm having my problem.

I get the normal list of boot messages and such flashing across the screen but when it pops up the login prompt, it keeps going with messages (exact screen output below) and seems to hang - almost as if the login prompt got displayed too soon.  The last thing it shows running on screen (/etc/rc.local) doesn't have anything out of the ordinary, just the default comments and exit 0.  Hitting enter when it seems to "hang" brings up the prompt and I'm able to log in fine at the moment, with just a fresh install + ssh, but once I start setting up my server with things like Apache, that doesn't work because it seems to get confused (ie: between the login prompt and entering my ssl password for https).  I've tried this on 2 different machines and it's the same on both.

Any help is greatly appreciated and I apologize in advance if this was answered elsewhere already and I missed it.

[snip]
* Starting kernel log...
Ubuntu 7.04 myServer tty1
myServer login: * Starting OpenBSD Secure Shell Server...
* Starting deferred execution scheduler atd
* Starting periodic command scheduler crond
* Running local boot scripts (/etc/rc.local) [blinky cursor]

---

### Post by introspectif on 2007-04-28
I've been wondering how to solve this too.

---

### Post by pewtermoose on 2007-04-30
Nobody has any info on this at all?

---

### Post by SlowYaRoll on 2007-05-01
Okay. . .I thought I was the only person having this problem.  *sheads tear*  I'M NOT ALONE!  What makes it even worse. . .I just moved from New Jersey to Georgia and all my replacement video cards are back in NJ.  I wanted to try swapping out cards, disabling the onboard video card, then install from scratch to see if that'd fix the issue.

:popcorn:

---

### Post by dcstar on 2007-05-01
> **pewtermoose said:**
> I recently installed Feisty server and I'm loving it except for an issue I'm having after the first login.  It installs fine and boots up and I log in.  I've done nothing else except for and apt-get update/upgrade and install ssh.  After that I happened to reboot and this is where I'm having my problem.

I get the normal list of boot messages and such flashing across the screen but when it pops up the login prompt, it keeps going with messages (exact screen output below) and seems to hang - almost as if the login prompt got displayed too soon.  The last thing it shows running on screen (/etc/rc.local) doesn't have anything out of the ordinary, just the default comments and exit 0.  Hitting enter when it seems to "hang" brings up the prompt and I'm able to log in fine at the moment, with just a fresh install + ssh, but once I start setting up my server with things like Apache, that doesn't work because it seems to get confused (ie: between the login prompt and entering my ssl password for https).  I've tried this on 2 different machines and it's the same on both.

Any help is greatly appreciated and I apologize in advance if this was answered elsewhere already and I missed it.

[snip]
* Starting kernel log...
Ubuntu 7.04 myServer tty1
myServer login: * Starting OpenBSD Secure Shell Server...
* Starting deferred execution scheduler atd
* Starting periodic command scheduler crond
* Running local boot scripts (/etc/rc.local) [blinky cursor]

If you think that something is starting up too soon (before another required item), go into your /etc/rc2.d directory and have a look at the list.

You can adjust the startup order by renaming the links (S0 first - S99 last etc.), everything in that directory is loaded for Run Level 2, but perhaps some items starting (like SSH) depend on another one that it actually set to start after it!

---

### Post by pelago on 2007-05-01
This happens to me too. If I just press Return a few times the login prompt comes back. Does that help?

---

### Post by pewtermoose on 2007-05-01
Thanks for the advice dcstar, but I'm not sure if that's the solution.  My /etc/rc2.d directory looked like this before hand:
```
README       S17mysql-ndb-mgm  S20makedev  S23ntp   S91apache2
S10sysklogd  S18mysql-ndb      S20rsync    S89atd   S99rc.local
S11klogd     S19mysql          S20ssh      S89cron  S99rmnologin
```

But I had to whittle it down to only sysklogd, klogd, atd and cron (and changing the S values on those to even lower) before it finally stopped. Also, even at the original values, should there really be a difference between the S17/8/9 mysql processes and the S20 ssh process?  MySQL started before the prompt was displayed while ssh wasn't. Unless of course, S19 is the magic threshold before the login prompt is shown (which I get the feeling it isn't).

> **pelago said:**
> This happens to me too. If I just press Return a few times the login prompt comes back. Does that help?

Yes and no, see my original post:
> Hitting enter when it seems to "hang" brings up the prompt and I'm able to log in fine at the moment, with just a fresh install + ssh, but once I start setting up my server with things like Apache, that doesn't work because it seems to get confused (ie: between the login prompt and entering my ssl password for https).

---

### Post by SlowYaRoll on 2007-05-01
> **pelago said:**
> This happens to me too. If I just press Return a few times the login prompt comes back. Does that help?

I just type in my login name and password, then it sort of fixes itself; it's just a little annoying since I'm not sure what's causing the problem.

Maybe when I buy a Dell with Ubuntu pre-loaded on it, this won't happen.  
[CENTER]:KS   :KS   :KS    :KS   :KS   :KS 

:guitar: [/CENTER]

---

