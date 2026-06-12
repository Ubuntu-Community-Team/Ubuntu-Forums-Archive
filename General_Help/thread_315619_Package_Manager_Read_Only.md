---
title: "Package Manager Read Only"
date: 2006-12-09
forum: General Help
---

### Post by TommyMann on 2006-12-09
Today, I got an error message from Adept Updater. Last night I was showing off Kubuntu to a potential user in a place without internet. I pulled up Adept to show him how easy it is to get free programs. Then I closed it, and closed updater for no appearant reason. Today I go to get the updates, and first I get an error with updater so then I try adept, and now I know something is wrong.

From Adept:
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

From Synaptic:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I looked the KSysGuard to see if there was something obvious to shut down. I tried telling updater not to come up at start up. I also tried doing it the windows way and restarting.

Any help here?

---

### Post by taurus on 2006-12-09
From a terminal, run

```
sudo dpkg --configure -a
```

---

### Post by VividHazE on 2006-12-10
Thanks taurus your a genius! I was just about to reinstall kubuntu before I found your fix. :)

---

### Post by taurus on 2006-12-10
> **VividHazE said:**
> Thanks taurus your a genius! I was just about to reinstall kubuntu before I found your fix. :)
Am I???  :-$

---

