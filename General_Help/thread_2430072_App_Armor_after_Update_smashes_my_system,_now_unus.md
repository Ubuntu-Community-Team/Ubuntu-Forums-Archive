---
title: "App Armor after Update smashes my system, now unusable"
date: 2019-10-27
forum: General Help
---

### Post by shutterfoot on 2019-10-27
Hey folks, I can no longer get into my xubuntu 18.04 installation on my netbook. Immediately after updates my resources were maxed out and I could no longer reliably move the cursor on the screen. I had to do a hard shutdown after 12 minutes of waiting and ctrl+alt+f1 > ctrl+alt+del ing. After a restart I see it hanging at an indefinite "LSB: AppArmor initialization (xx:xx/no limit)" start job. Oddly the system will eventually get to a log in screen but be unusable. It seems app armor is maxing out my 1 gig of ram, and then just punishing swap until it can't take it no more! I'm wondering if anyone else using a low ram system has been experiencing the same thing. I've tried reinstalling apparmor (in cli upstart mode), and when I do I get a handful of "Out of Memory: Kill process xxxx (apparmor_parsor)" notices. In upstart mode the device and terminal snap free experience is superb. But I've gone all-in on snaps! I'm curious if this is a wider problem for low ram systems running apparmor, but I haven't found a bug report yet, and as stated I haven't had a problem before and I was quick to adopt snaps into my system. My hardware is fine too as Xubuntu 16.04 still runs like a champ on it. So looking forward, I can nuke and pave, but will I still be able to run snaps and is it even possible or worth the trouble to install Ubuntu minus snap.d and apparmor? 

The Hardware is an Atom N450 Netbook w/ 1gb ram, and I'd like to know if:

Anyone running Ubuntu on <1g ram and having/not having a problem with apparmor?

Is it problematic or troublesome to remove snap.d and apparmor from my current Xubuntu installation?

Or am I missing something and Apparmor may not be the problem after all?


**Edit: This is the wrong category, should be moved to general help I believe, it pertains to a software update, not an upgrade! So sorry..**

---

### Post by uRock on 2019-10-27
Moved to General Help.

For future reference, use the report button to get our attention to move the thread. :p

---

