---
title: "What's up with Timevault dev?"
date: 2008-03-20
forum: General Help
---

### Post by fictivetoast on 2008-03-20
Anyone know what's going on with Timevault?  64-bit debs of the 7.5 release STILL aren't available, and the launchpad site doesn't seem to've been updated since late last year... has work stalled?

Just curious - it looked like an excellent application, and I'm a bit sad to see it flounder.

---

### Post by fictivetoast on 2008-05-09
BUMP?

The dev pages still haven't changed over on launchpad...

---

### Post by Dyqik on 2008-05-16
Hi,

I've just managed to install timevault 0.7.5 on x64 Hardy by just forcing the  install of the x86 package with sudo dpkg -i --force-all timevault[...].deb

It seems to be working OK (as it should, it's all written in python so there are no architecture issues).  

I think the missing devs made a bit of a mistake releasing it as x86 only, it should have been a cross platform package, although maybe they didn't have a x64 box to test it on.

---

### Post by fictivetoast on 2008-05-16
hmm, I've force-installed it and think I've resolved dependencies, but the crash detector still seems to think Timevault is dying all the time, and I can't get the snapshot daemon to actually do anything...

---

### Post by Dyqik on 2008-05-18
It took a reboot to make sure that the backend daemon and the notifier were working from the same script with 0.7.5 for me.  I did get one or two crash notifications, after which everything started working.

I also had to make sure that most of the .* directories that are used as caches of various sorts were excluded (particularly .cxoffice and .wine - .mozilla is excluded by default) to get the baseline snapshorts to work in a sane amount of time.

---

### Post by AstralPancakes on 2008-05-20
Just to save anyone finding this thread after me the trouble I just went through: installing with --force-all doesn't take care of dependencies for you. You need to install at least python-pysqlite2 and python-gamin over the default packages, and possibly some or all of the packages the wiki page mentions under depends.

---

### Post by Dyqik on 2008-06-06
Possibly --force-architecture is a better option then, as dpkg etc. should then get the dependencies.

---

