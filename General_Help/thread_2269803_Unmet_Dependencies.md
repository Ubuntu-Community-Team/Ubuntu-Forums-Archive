---
title: "Unmet Dependencies"
date: 2015-03-18
forum: General Help
---

### Post by clutch2 on 2015-03-18
Hello,

So when I'm trying to install a program I get the unmet dependencies error. I've had this problem before with other programs. I've searched forums and found fixes from others for the specific program. I would like to try to understand these better so that I may be able to figure these out through troubleshooting instead of going to others for help. So with the following error, I'd like to do a sanity check and make sure I'm understanding what it's saying. Also, are there any general steps that are usually taken when autoclean, dkgp --configure -a, and apt-get -f install don't work?

The following packages have unmet dependencies:
 libfolks25 : Breaks: libfolks-eds25 (< 0.8.0-2~) but 0.6.9-1+b1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Looks like libfolks25 will break libfolks-eds25. I'm not sure what (< 0.8.0-2~) is referring too. I assume its a package. And finally, 0.6.9-1+b1 (assuming another package) is going to be installed, but is that what is "breaking" it?

Thanks for your time

---

### Post by Holger_Gehrke on 2015-03-18
The numbers are version numbers. Are you installing from a PPA or from a downloaded .deb file ? The stuff in the repositories usually is checked for version conflicts, but PPAs can get out of step with the upgrades ...

---

### Post by mc4man on 2015-03-18
Check & or post - 
```
apt-cache policy  libfolks25 libfolks-eds25
```
0.6.x is around the time of 12.10, what release of Ubuntu are you using?

---

### Post by clutch2 on 2015-03-18
My apologies gentlemen. I'm using Debian and not Ubuntu on this machine. :mad: 

Your posts did help me understand the error output more. But seeing as how I'm in the wrong place, we can end the thread here.

Again, sorry for the misdirection.

---

